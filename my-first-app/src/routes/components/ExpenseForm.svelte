<script>
  let amount = $state('');
  let category = $state('Food');

  let { onAddExpense } = $props();

  function submit() {
    if (amount <= 0) return;

    onAddExpense(amount, category);

    amount = '';
  }
</script>

<form
  onsubmit={(event) => {
    event.preventDefault();
    submit();
  }}
>
  <input
    type="number"
    bind:value={amount}
    placeholder="Enter amount"
  />

  <select bind:value={category}>
    <option>Food</option>
    <option>Travel</option>
    <option>Shopping</option>
  </select>

  <button type="submit">
    Add Expense
  </button>
</form>