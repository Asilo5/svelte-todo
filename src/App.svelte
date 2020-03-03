<script>
	
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
  ]

</script>

<main>
  <section class='container'>
	<input type='text' class='todo-input' placeholder='What needs to be done' />

 {#each todos as todo}
	<section class='todo-item'> 
		<section class='todo-item-left'>
			<input type='checkbox' />
			<p class='todo-item-label'>{todo.title}</p>
		</section>
		<p class='remove-item'>
			&times;
		</p>
	</section>
   {/each}
 </section>

  <section class='extra-container'>
     <div><label><input type='checkbox' /> Check All </label></div>
	 <p>3 times left</p>
  </section>

  <section class='extra container'>
     <section>
	 
	 </section>
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
	
</style>