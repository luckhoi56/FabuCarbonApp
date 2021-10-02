<script>
  import { Tile, Button } from "carbon-components-svelte";
  import { Grid, Row, Column } from "carbon-components-svelte";
  import DetailButton from "./DetailButton.svelte";
  export let order_number=""
  export let m_items=""


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
        <Column style="text-align:center">Tên Khách Hàng</Column>
      </Row>
      <br />
      <Row>
        <Column style="text-align:center">
          <DetailButton m_items={m_items} />
        </Column>
      </Row>
      <br />
      <br />
      
      
    </Grid>
  </Tile>

  <br />

</main>
