<script>
  let { expense, onDelete } = $props();

  let isImportant = $state(false);
</script>

<div>
  <span>
    ₹{expense.amount} - {expense.category}
  </span>

  <button onclick={() => isImportant = !isImportant}>
    {isImportant ? '⭐' : '☆'}
  </button>

  <button onclick={() => onDelete(expense.id)}>
    Delete
  </button>
</div>