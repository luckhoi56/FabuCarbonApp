
<script>
    import { Tile, Button } from "carbon-components-svelte";
    let m_status ="N/A"
    async function open(){
        const response = await fetch("https://yume-angular.herokuapp.com/getDSTOn")
        //let m_reply_confirm = await response.json()
    }

    async function close(){
        const response = await fetch("https://yume-angular.herokuapp.com/getDSTOff")
        //let data = await response.json()
    }

    async function checkStatus(){
        console.log("check status is clicked on android side")
        const response = await fetch("https://yume-angular.herokuapp.com/getDSTStatus")
        let data = await response.json();
        console.log(data)
        //checkStatus = status.status
        if(data.daylight == 1)
            m_status ="On"
        if(data.daylight == 0)
            m_status ="Off"

    }
</script>

<h1>Daylight Saving Time</h1>
<main>
    <Button on:click={open}>Turn on DST </Button>
    <Button on:click={close}>Turn off DST</Button>
    <br>
    <Button on:click={checkStatus}>{m_status}</Button>

</main>

<style>

</style>