<script lang="ts">
let expensesInput: string = '';
let outputMessage: string = '';

// Function to process and display expenses
$: {
    let expensesList: number[] = [];
    let newExpensesList: string[] = expensesInput.split(" ");
    let total: number = 0;

    // Convert each expense to an integer and add it to the expenses list
    for (let i = 0; i < newExpensesList.length; i++) {
        let expense = parseInt(newExpensesList[i]);
        if (!isNaN(expense)) { // Only add valid numbers
            expensesList.push(expense);
        }
    }

    // Calculate the total expenses
    for (let i = 0; i < expensesList.length; i++) {
        total += expensesList[i];
    }

    // Construct the output message
    outputMessage = `Expenses: ${expensesList.join(', ')}\nTotal: $${total}`;

}
</script>

<h1>Did I spend too much?</h1>
<input type="text" bind:value={expensesInput} placeholder="Enter expenses">
<pre>{outputMessage}</pre>
