<script>

  const ENTER_KEY = 13;
  const ESCAPE_KEY = 27;

  let newTodo = '';
	
  let todos = [
	  {
		  id: 1,
		  completed: false,
		  title: 'Make Svelte project practice',
		  editing: false
	  },
	  {
		  id: 2,
		  completed: false,
		  title: 'Study for mock interview interview',
		  editing: false
	  },
	  {
		  id: 3,
		  completed: false,
		  title: 'Make Svelte project for school',
		  editing: false
	  },
	  {
		  id: 4,
		  completed: false,
		  title: 'Get haircut',
		  editing: false
	  }
  ];


  const addTodo = (e) => {
    if(e.which === ENTER_KEY){
       todos.push({
		  id: todos.length + 1,
		  completed: false,
		  title: newTodo,
		  editing: false
	   });

	   todos = todos;
	   newTodo = '';
	}
  }

  const deleteTodo = (id) => {
    todos = todos.filter((todo)=> todo.id !== id);
  }

  const checkAllTodos = (e) => {
	todos.forEach((todo)=> todo.completed = e.target.checked);
	todos = todos;
  }

  $: todosRemaining = todos.filter((todo) => !todo.completed).length;

</script>

<main>
  <section class='container'>
	<input bind:value={newTodo} 
	      on:keydown={addTodo}
	      type='text' 
		  class='todo-input' 
		  placeholder='What needs to be done' />

 {#each todos as todo}
	<section class='todo-item'> 
		<section class='todo-item-left'>
			<input type='checkbox' bind:checked={todo.completed}/>
			<p class='todo-item-label' class:completed={todo.completed}>{todo.title}</p>
		</section>
		<p class='remove-item' on:click={()=>deleteTodo(todo.id)}>
			&times;
		</p>
	</section>
   {/each}
 </section>

  <section class='extra-container'>
     <div><label><input type='checkbox' on:change={checkAllTodos} /> Check All </label></div>
	 <p>{todosRemaining} times left</p>
  </section>

  <section class='extra container'>
     <section>
	   <button>All</button>
	   <button>Active</button>
	   <button>Completed</button>
	 </section>
  </section>

  <section>
    <button>Clear Completed</button>
  </section>

</main>

<style type="text/scss">
	.todo-item {
		display: flex;
		justify-content: space-between;
		width: 40%;
		background-color: aquamarine;
		margin: 10px;
	}

	.todo-item-left {
			display: flex;
			justify-content: space-between;
			width: 50%;
	}

	.completed {
		text-decoration: line-through;
	}
	
</style>