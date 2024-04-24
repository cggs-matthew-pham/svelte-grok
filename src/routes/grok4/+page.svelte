<script lang="ts">

    let name = '';
    let message = '';

    $: {
        if (name === '') {
            message = 'Welcome! May I know your name?';
        } else if (name.length <= 3) {
            message = `Hi ${name}, you have a short name.`;
        } else if (name.length >= 4 && name.length <= 8) {
            message = `Hi ${name}, nice to meet you.`;
        } else {
            message = `Hi ${name}, you have a long name.`;
        }
    }
</script>

<h1>Short/Long Names</h1>

<form>
    <label for="name">Enter your name:</label>
    <input type="text" id="name" name="name" bind:value="{name}">
</form>

<pre>{message}</pre>