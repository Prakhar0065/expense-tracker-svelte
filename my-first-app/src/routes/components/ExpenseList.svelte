<script>
  import ExpenseItem from './ExpenseItem.svelte';

  let { expenses, onDelete } = $props();
</script>

{#if expenses.length === 0}

  <p>No expenses found.</p>

{:else}

  {#each expenses as expense}

    <ExpenseItem
      {expense}
      onDelete={onDelete}
    />

  {/each}

{/if}