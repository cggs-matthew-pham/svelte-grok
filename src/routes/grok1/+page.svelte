<script lang="ts">
    let friend1 = "";
    let friend2 = "";
    let friend3 = "";

    $: message = `Hello, young ${friend1}\nHello, brave ${friend2}\nHello, wise ${friend3}`;
</script>

<h1>Hello to you three!</h1>
<form>
    <label for="friend1">Friend 1:</label>
    <input type="text" id="friend1" bind:value={friend1}><br>
    <label for="friend2">Friend 2:</label>
    <input type="text" id="friend2" bind:value={friend2}><br>
    <label for="friend3">Friend 3:</label>
    <input type="text" id="friend3" bind:value={friend3}><br>
</form>
<pre>{message}</pre>