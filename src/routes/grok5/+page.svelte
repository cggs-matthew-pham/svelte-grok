<script>
let cheer = '';
let cheerOutput = '';

// Inline reactive statement to compute the cheer message using a loop
$: {
    cheerOutput = '';
    for (let i = 0; i < cheer.length; i++) {
        const letter = cheer[i];
        cheerOutput += `Give me a ${letter}, ${letter}!\n`;
    }
    cheerOutput += cheer ? `What does it spell?\n${cheer.toUpperCase()}` : '';
}
</script>

<h1>Give me a G!</h1>
<form>
    <label for="cheerInput">Cheer:</label>
    <input type="text" id="cheerInput" bind:value={cheer}>
</form>
<pre>{cheerOutput}</pre>
