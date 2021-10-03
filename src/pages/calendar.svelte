<script>
    import { DataTable } from "carbon-components-svelte";
  </script>
  
  <DataTable
    headers={[{ key: 'name', value: 'Name' }, { key: 'protocol', value: 'Protocol' }, { key: 'port', value: 'Port' }, { key: 'rule', value: 'Rule' }]}
    rows={[{ id: 'a', name: 'Load Balancer 3', protocol: 'HTTP', port: 3000, rule: 'Round robin' }]}
  />