<script>
  import Clock from './clock.svelte';
  import Todo from './todolista.svelte';
  import { todolista } from './todostore.js';
  import API from './API.svelte';

  let newTodo = '';

  function addTodo() {
    if (newTodo) {
      todolista.update((todos) => [...todos, newTodo]);
      newTodo = '';
    }
  }
</script>

<body>
  <main>
    <Clock />

    <API />
    <div class="todo">
      <Todo />
      <input bind:value={newTodo} />
      <button on:click={addTodo}>Lisää</button>
    </div>
  </main>
</body>

<style>
  body {
    background-color: rgb(255, 161, 0, 0.3);
  }
  .todo {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    position: fixed;
    flex-direction: column;
    top: 10px;
    right: 10px;
    padding-right: 8em;
    padding-top: 5em;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS',
      sans-serif;
    font-size: 1.2em;
  }
  button {
    margin-top: 1em;
    padding-left: 20px;
    padding-right: 20px;
    border-radius: 20px;
    background-color: black;
    color: white;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
