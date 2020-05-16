<script>
  import { createEventDispatcher } from 'svelte';
  export let todo;

  const dispatch = createEventDispatcher();
</script>

<div class="todo-card">
  <h5>{todo.title}</h5>
  <div>
    <input
      type="checkbox"
      name="completed"
      bind:checked={todo.completed}>
    {#if todo.completed}
      Complété
    {:else}
      Non complété
    {/if}
  </div>
  <button on:click={() => dispatch('deleteTodo', todo.id)}>Supprimer</button>
</div>

<style>
  .todo-card {
    min-width: 200px;
    border-style: solid;
    border-width: 2pxb;
    border-color: darkgrey;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  button {
    background-color: red;
  }
</style>