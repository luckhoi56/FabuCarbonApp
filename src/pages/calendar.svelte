<script>
    import { DataTable,Tag } from "carbon-components-svelte";
    import { onMount } from "svelte";
    import spacetime from 'spacetime'
    import{_} from 'lodash'
  
    var m_sorted_date = ''
    var appointments = ''
    async function getAppoinments() {
    const res = await fetch("https://burineyelash.s3.us-west-1.amazonaws.com/databaseFile/data.json")
    
    return res.json()
    
  }
  const compare_date = (a,b) =>{
    let date_a = spacetime(a)
    let date_b = spacetime(b)
    if(date_a.isBefore(date_b)){
      return -1
    }
    else if(date_a.isSame(date_b)){
      return 0
    }
    else
      return 1
  }

  const compare_time = (a,b) => {
    var date_a = spacetime(`March 1 2012 ${a.Time}`, 'America/Los_Angeles')
    var date_b = spacetime(`March 1 2012 ${b.Time}`, 'America/Los_Angeles')
    
    if(date_a.isBefore(date_b)){
      return -1
    }
    else if(date_a.isSame(date_b)){
      return 0
    }
    else
      return 1

  }
  //process give a new array
  const process = (m_object) =>{
    
     for (let [key,values] of Object.entries(m_object)){
       
      let m_array = []
      for(let i = 0; i < values.length; i++){
        let temp= {
          id:i,
          Customer: values[i].firstName + " " + values[i].lastName,
          Phone: values[i].phoneNumbers,
          Time: values[i].time,
          Service: values[i].service,
          Technician: values[i].technician,
        }
        m_array.push(temp)
      }
      m_object[key] = m_array
    }
  }

  const filterPastDate = (dates) =>{

    let m_current_date = spacetime.now('America/Los_Angeles')
    dates.filter(date=>{
      let m_date = spacetime(date+" " + m_current_date.time()) //make them the same time so you can only compare date
      if(m_date.isAfter(m_current_date) || m_date.isSame(m_current_date,'date')){
        console.log(m_date.date())
        console.log('bitch')
        return date
      }
        
    })
  
  }
  onMount(async () => {
		let temps = await getAppoinments()
    appointments = _.groupBy(temps, temp => temp.date);
    process(appointments)
    m_sorted_date = Object.keys(appointments)
    m_sorted_date.sort(compare_date)
    filterPastDate(m_sorted_date)

    for(let value of Object.values(appointments)){
      value.sort(compare_time)
    }

	});

  let d = spacetime.now('America/Los_Angeles') 
  </script>
  
  {#each m_sorted_date as key}
  <Tag type="high-contrast">{key}</Tag>
  <br>
  <DataTable
    headers={[
      { key: 'Time', value: 'Time' },
      { key: 'Technician', value: 'Technician' },
      { key: 'Service', value: 'Service' },
      { key: 'Customer', value: 'Customer' },
      { key: 'Phone', value: 'Phone' } 
      ]}
    rows={appointments[key]}
  />
  <br>
  <br>
  <br>
  {/each}





