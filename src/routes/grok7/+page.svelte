<script lang="ts">
import {
    onMount
} from 'svelte';

let stepSize: number = 10; // Default step size
let canvas: HTMLCanvasElement;
let ctx: CanvasRenderingContext2D | null;

onMount(() => {
    ctx = canvas.getContext('2d');
    drawStaircase();
});

$: if (ctx && stepSize > 0) {
    drawStaircase();
}

function drawStaircase(): void {
    if (ctx) {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.beginPath();
        let x = 0;
        let y = 0;
        ctx.moveTo(x, y);
        while (x < 150 && y < 150) {
            x += stepSize;
            ctx.lineTo(x, y);
            y += stepSize;
            ctx.lineTo(x, y);
        }
        x = 0;
        ctx.lineTo(x, y);
        ctx.closePath();
        ctx.stroke();
    }
}
</script>

<style>
canvas {
    border: 1px solid black;
}
</style>

<h1>Up the downstair</h1>
<form>
    <label for="stepSize">Step Size (Max 50):</label>
    <input type="number" bind:value={stepSize} min="1" max="50" id="stepSize">
</form>
<canvas bind:this={canvas} width="250" height="250"></canvas>
