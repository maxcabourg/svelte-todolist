<script>
  import Todo from './Todo.svelte';
  import AddTodo from './AddTodo.svelte';

  let todos = [{
    id: 1,
    title: 'Todo 1',
    completed: false
  }, {
    id: 2,
    title: 'Todo 2',
    completed: true
  }];

  $: length = todos.length;

  const addTodo = event => {
    todos = [...todos, {
      id: todos.length + 1,
      title: event.detail,
      completed: false
    }];
  }

  const deleteTodo = event => {
    todos = todos.filter(todo => todo.id !== event.detail);
  }
</script>

<main>
	<h2>My todos ({length})</h2>
  <div class="todolist">
    {#each todos as todo}
      <Todo todo={todo} on:deleteTodo={deleteTodo}/>
    {/each}
  </div>
  <div class="add-todo">
    <AddTodo on:addTodo={addTodo}/>
  </div>
</main>

<style>
  h2 {
    text-align: center;
  }

  .add-todo {
    display: flex;
    justify-content: center;
  }

  .todolist {
    display: flex;
    justify-content: space-around;
  }
</style>