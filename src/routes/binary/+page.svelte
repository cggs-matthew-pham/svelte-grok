<script lang="ts">
import {
    onMount
} from 'svelte';

let binaryString: string = '';
let userAnswer: string = '';
let feedback: string = '';
let correctAnswer: number;
let score: number = 0;

onMount(() => {
    generateNewBinary();
});

function generateNewBinary(): void {
    const randomNumber = Math.floor(Math.random() * 16); // Generates a number from 0 to 15
    binaryString = randomNumber.toString(2).padStart(4, '0'); // Converts number to binary, ensures it's 4 bits
    correctAnswer = randomNumber;
}

function checkAnswer(): void {
    const parsedAnswer = parseInt(userAnswer);
    if (parsedAnswer === correctAnswer) {
        feedback = 'Correct! Well done!';
        score++;
        generateNewBinary(); // Generate a new binary number regardless of whether the answer was correct
        userAnswer = ''; // Reset user input field

    } else {
        feedback = 'Incorrect, keep trying!';
    }
}


$: if (userAnswer.length > 0 && !isNaN(Number(userAnswer))) {
    checkAnswer();
}
</script>

<h1>Binary Conversion Game</h1>
<p>Convert the binary number to decimal:</p>
<strong>{binaryString}</strong>

<form on:submit|preventDefault={checkAnswer}>
    <input type="text" bind:value={userAnswer} placeholder="Enter decimal number" />
</form>

<p>{feedback}</p>
<pre>Score: {score}</pre>

<style>
input {
    font-size: 16px;
    padding: 5px;
    margin: 5px;
}

strong {
    font-size: 20px;
    color: blue;
}
</style>
