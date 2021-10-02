<script>
  import { Button, Modal } from "carbon-components-svelte";
  export let m_items = "";
  export let open = false;
</script>

<Button size="small" kind="tertiary" on:click={() => (open = true)}>
  Chi Tiet
</Button>

<Modal
  size="xs"
  bind:open
  modalHeading="Chi Tiet"
  secondaryButtonText="Ok"
  on:click:button--secondary={() => (open = false)}
  on:open
  on:close
  on:submit>
  <div>
    {#each m_items as item}
      <li> {item.Quantity} {item.chosenSize} {item.ItemName}: {item.chosenTopping} </li>
    {/each}
  </div>
</Modal>
