<script>
  import { Tile, Button } from "carbon-components-svelte";
  import { Grid, Row, Column } from "carbon-components-svelte";
  import DetailButton from "./DetailButton.svelte";
  export let order_number=""
  export let m_items=""
  export let customer_name=""
  async function finishOrder(){
    console.log("Cusomter finish is:" +order_number )
    
    const res = await fetch("https://yume-angular.herokuapp.com/finishOrder",{
      headers:{
        'Content-Type': 'application/json'
      },
      method: 'POST',
      body: JSON.stringify({
	      "number": order_number
      })
      
    });
    const json = await res.json()
    console.log(json)
    document.getElementById(order_number).remove()
  }
</script>

<style>

</style>

<main >
  <Tile id={order_number}>
    <Grid>
      <Row>
        <Column style="text-align:center">So Order: {order_number}</Column>
      </Row>
      <br />
      <Row>
        <Column style="text-align:center">Tên Khách Hàng: {customer_name}</Column>
      </Row>
      <br />
      <Row>
        <Column style="text-align:center">
          <DetailButton m_items={m_items} />
        </Column>
      </Row>
      <br />
      <br />
      
      <Row>
        <Column style="text-align:center">
          <Button size="small"  kind="danger" on:click={finishOrder} >San Sang</Button>
        </Column>
      </Row>
    </Grid>
  </Tile>

  <br />

</main>
