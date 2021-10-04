<script>
    import { DataTable } from "carbon-components-svelte";
    import { onMount } from "svelte";
    import{_} from 'lodash'
    async function getAppoinments() {
    const res = await fetch("https://burineyelash.s3.us-west-1.amazonaws.com/databaseFile/data.json")
    return res.json()
  }
  onMount(async () => {
		let appointments = await getAppoinments()
    const grouped = _.groupBy(appointments, appoinment => appoinment.date);
    console.log(grouped)
	});
  </script>
  
  <DataTable
    headers={[{ key: 'Customer', value: 'Customer' }, { key: 'technician', value: 'Technician' }, { key: 'time', value: 'Time' }, { key: 'rule', value: 'Rule' }]}
    rows={[{ id: 'a', name: 'Load Balancer 3', protocol: 'HTTP', port: 3000, rule: 'Round robin' }]}
  />