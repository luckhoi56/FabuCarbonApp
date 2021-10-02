<script>
  import { Button, TextArea } from "carbon-components-svelte";
  async function sendAnnouncement() {
    console.log("got clicked")
    const res = await fetch("http://localhost:4242/send-announcement", {
      headers: {
        "Content-Type": "application/json"
      },
      method: "POST",
      body: JSON.stringify({
        reason: document.querySelector("TextArea").value
      })
    });
    document.querySelector("TextArea").value = "";
  }
</script>

<style>

</style>

<main>
  <TextArea
    labelText="App description"
    placeholder="Enter a description..."
     />
  <Button on:click={sendAnnouncement}>Send</Button>
</main>
