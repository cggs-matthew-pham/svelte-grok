<script lang="ts">
    let isRaining: boolean = false;
    let distance: number | undefined = undefined;
    let message: string = "";

    $: {
        if (isRaining) {
            message = "You should take the bus.";
        } else if (distance === 0 || distance === undefined) {
            message = "Enter the distance to travel OR check if it's raining.";
        } else if (distance > 10) {
            message = "You should take the bus.";
        } else if (distance >= 2) {
            message = "You should ride your bike.";
        } else {
            message = "You should walk.";
        }
    }
</script>

<h1>Method of transportation</h1>
<form>
    <label for="isRaining">Is it currently raining?</label>
    <input type="checkbox" id="isRaining" bind:checked={isRaining}><br><br>
    <label for="distance">Enter the distance you need to travel (in km):</label>
    <input type="number" id="distance" bind:value={distance} disabled={isRaining}><br>
</form>
<pre>{message}</pre>
