<script>
  import YumeCardFinish from "../components/YumeCardFinish.svelte";

  export let name;
  let m_filtered_orders = [];
  async function onButtonTap() {
    const response = await fetch("https://yume-angular.herokuapp.com/getFinishOrder");

    let order_queue = await response.json();

    let filtered_order_queue = order_queue;
    for (let order of filtered_order_queue) {
      order.content = filterOrder(order.content);
	}
	m_filtered_orders = filtered_order_queue
	//console.log()
  }

  function filterOrder(orders_queue) {
    let m_items = [];

    for (let item of orders_queue) {
      if (item.Quantity > 0) m_items.push(item);
    }
    return m_items;
  }
</script>

<style>

  
</style>

<main>
  <h1>Order Da Hoan Thanh</h1>
  <button text="tap me now" on:click={onButtonTap}>Tap Me</button>
  {#each m_filtered_orders as order}
    <YumeCardFinish m_items={order.content} order_number={order.orderNumber} customer_name={order.customerName}/>
    
  {/each}

</main>
