<script>
  import ExpenseForm from './components/ExpenseForm.svelte';
  import ExpenseList from './components/ExpenseList.svelte';

  let expenses = $state([]);

  let filter = $state('All');

  let total = $derived(
    expenses.reduce((sum, expense) => sum + expense.amount, 0)
  );

  let filteredExpenses = $derived(
    filter === 'All'
      ? expenses
      : expenses.filter(expense => expense.category === filter)
  );

  function addExpense(amount, category) {
    expenses.push({
      id: Date.now(),
      amount: Number(amount),
      category
    });
  }

  function deleteExpense(id) {
    expenses = expenses.filter(expense => expense.id !== id);
  }
</script>

<h1>💰 Expense Tracker</h1>

<ExpenseForm onAddExpense={addExpense} />

<h2>Total: ₹{total}</h2>

<div>
  <button onclick={() => filter = 'All'}>All</button>
  <button onclick={() => filter = 'Food'}>Food</button>
  <button onclick={() => filter = 'Travel'}>Travel</button>
  <button onclick={() => filter = 'Shopping'}>Shopping</button>
</div>

<ExpenseList
  expenses={filteredExpenses}
  onDelete={deleteExpense}
/>