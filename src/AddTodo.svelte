<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let title = '';

  const addTodo = () => {
    dispatch('addTodo', title);
  }

</script>

<form on:submit|preventDefault={addTodo}>
  <input type="text" bind:value={title}>
  <button type="submit">Ajouter</button>
</form>

<style>

</style>