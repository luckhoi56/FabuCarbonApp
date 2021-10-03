<script>
    import { DataTable } from "carbon-components-svelte";
  </script>
  
  <DataTable
    headers={[{ key: 'Customer', value: 'Customer' }, { key: 'technician', value: 'Technician' }, { key: 'time', value: 'Time' }, { key: 'rule', value: 'Rule' }]}
    rows={[{ id: 'a', name: 'Load Balancer 3', protocol: 'HTTP', port: 3000, rule: 'Round robin' }]}
  />