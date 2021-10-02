<script>
    import { Button, TextArea } from "carbon-components-svelte";
    async function sendReasonToClose() {
      console.log("got clicked")
      const res = await fetch("https://yume-angular.herokuapp.com/addBackCategory", {
        headers: {
          "Content-Type": "application/json"
        },
        method: "POST",
        body: JSON.stringify({
          "Category": document.querySelector("TextArea").value
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
    <Button on:click={sendReasonToClose}>Send</Button>
  </main>
  