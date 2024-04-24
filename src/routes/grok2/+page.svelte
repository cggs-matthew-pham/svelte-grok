<script lang="ts">
    let message = "";
    let repeatCount = 0;
    let output = "";

    $: {
        output = "";
        for (let i = 0; i < repeatCount; i++) {
            output += `${message}\n`;
        }
    }
</script>

<h1>Repeaterbot</h1>
<form>
    <label for="message">What do you want me to say?</label>
    <input type="text" id="message" bind:value={message}><br><br>
    <label for="repeatCount">How many times do you want me to say it?</label>
    <input type="number" id="repeatCount" bind:value={repeatCount}><br><br>
</form>
<pre>{output}</pre>
