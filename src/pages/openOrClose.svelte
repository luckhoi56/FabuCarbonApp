<script>
    import { Tile, Button } from "carbon-components-svelte";
    let m_status ="N/A"
    async function open(){
        const response = await fetch("https://yume-angular.herokuapp.com/openRestaurant")
        //let m_reply_confirm = await response.json()
    }

    async function close(){
        const response = await fetch("https://yume-angular.herokuapp.com/closeRestaurant")
        //let data = await response.json()
    }

    async function checkStatus(){
        console.log("check status is clicked on android side")
        const response = await fetch("https://yume-angular.herokuapp.com/statusRestaurant")
        let data = await response.json();
        console.log(data)
        //checkStatus = status.status
        if(data.status == false)
            m_status ="Closed"
        else
            
            m_status ="Opened"
    }
</script>


<main>
    <Button on:click={open}>Mo Cua </Button>
    <Button on:click={close}>Dong Cua</Button>
    <br>
    <Button on:click={checkStatus}>{m_status}</Button>

</main>

<style>

</style>