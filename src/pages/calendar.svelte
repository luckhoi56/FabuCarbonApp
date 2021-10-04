<script>
    import { DataTable } from "carbon-components-svelte";
    import { onMount } from "svelte";
    import spacetime from 'spacetime'
    import{_} from 'lodash'
    var appointments = ''
    async function getAppoinments() {
    const res = await fetch("https://burineyelash.s3.us-west-1.amazonaws.com/databaseFile/data.json")
    return res.json()
    
  }
  onMount(async () => {
		appointments = await getAppoinments()
    const grouped = _.groupBy(appointments, appointment => appointment.date);
    console.log(grouped)
	});

  let d = spacetime.now('America/Los_Angeles')
  console.log(d.format('nice'))
  </script>
  
  {#each appointments as appointment}
  <DataTable
    headers={[{ key: 'Customer', value: 'Customer' }, { key: 'technician', value: 'Technician' }, { key: 'time', value: 'Time' }, { key: 'rule', value: 'Rule' }]}
    rows={[{ id: 'a', name: 'Load Balancer 3', protocol: 'HTTP', port: 3000, rule: 'Round robin' }]}
  />
  {/each}



