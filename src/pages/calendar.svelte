<script>
    import { DataTable } from "carbon-components-svelte";
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
    var date_a = spacetime(`March 1 2012 ${a}`, 'America/Los_Angeles')
    var date_b = spacetime(`March 1 2012 ${b}`, 'America/Los_Angeles')
    
    console.log(date_a)
    if(date_a.isBefore(date_b)){
      return -1
    }
    else if(date_a.isSame(date_b)){
      return 0
    }
    else
      return 1

  }
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

  onMount(async () => {
		let temps = await getAppoinments()
    appointments = _.groupBy(temps, temp => temp.date);
    process(appointments)
    m_sorted_date = Object.keys(appointments)
    m_sorted_date.sort(compare_date)
    

    for(let value of Object.values(appointments)){
      value.sort(compare_time)
    }

	});

  let d = spacetime.now('America/Los_Angeles')
  </script>
  
  {#each Object.keys(appointments) as key}
  <h1>{key}</h1>
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
  {/each}





  <!-- This example requires Tailwind CSS v2.0+ -->
<div class="flex flex-col">
  <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
    <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
      <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
        <table class="min-w-full divide-y divide-gray-200">
          <thead class="bg-gray-50">
            <tr>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Name
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Title
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Email
              </th>
              <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
                Role
              </th>
              <th scope="col" class="relative px-6 py-3">
                <span class="sr-only">Edit</span>
              </th>
            </tr>
          </thead>
          <tbody class="bg-white divide-y divide-gray-200">
            <tr>
              <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                Jane Cooper
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                Regional Paradigm Technician
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                jane.cooper@example.com
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                Admin
              </td>
              <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                <a href="#" class="text-indigo-600 hover:text-indigo-900">Edit</a>
              </td>
            </tr>

            <!-- More people... -->
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>
