<script lang="ts">
let word1: string = '';
let word2: string = '';
let outputMessage: string = '';

// Reactive statement to check anagram whenever word1 or word2 changes
$: {
    outputMessage = checkAnagram(word1, word2);
}

function checkAnagram(word1: string, word2: string): string {
    // Check if both words are entered
    if (!word1 || !word2) {
        return "Please enter both words to check if they are anagrams.";
    }

    const letters1 = Array.from(word1).sort();
    const letters2 = Array.from(word2).sort();
    const sortedWord1 = letters1.join('');
    const sortedWord2 = letters2.join('');

    // Check if the sorted letters match
    if (sortedWord1 === sortedWord2) {
        // Further check if the first and last characters of the words match
        if (word1[0] === word2[0] && word1[word1.length - 1] === word2[word2.length - 1]) {
            return 'Super Anagram!';
        } else {
            return 'Huh?';
        }
    } else {
        return 'Huh?';
    }
}
</script>

<h1>Super Anagram!</h1>
<form>
    <label for="word1">Word 1:</label>
    <input type="text" bind:value={word1} id="word1">
    <label for="word2">Word 2:</label>
    <input type="text" bind:value={word2} id="word2">
</form>
<pre>{outputMessage}</pre>
