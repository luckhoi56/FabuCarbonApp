<script>
    import { Button, TextArea } from "carbon-components-svelte";
    async function sendReasonToClose() {
      console.log("got clicked")
      const res = await fetch("https://yume-angular.herokuapp.com/getRemovedCategory", {
        headers: {
          "Content-Type": "application/json"
        },
        method: "GET"
      });
      document.querySelector("TextArea").value = await res.json();
    }
  </script>
  
  <style>
  
  </style>
  
  <main>
    <TextArea
      labelText="App description"
      placeholder="Enter a description..."
       />
    <Button on:click={sendReasonToClose}>Send</Button>
  </main>
  