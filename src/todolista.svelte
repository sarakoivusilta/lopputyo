<script>
  import { onMount, onDestroy } from 'svelte';
  import { todolista } from './todostore.js';

  let unsubscribe;
  let todos = [];

  onMount(() => {
    unsubscribe = todolista.subscribe((updatedTodos) => {
      todos = updatedTodos;
    });

    return () => {
      unsubscribe();
    };
  });

  onDestroy(() => {
    unsubscribe();
  });

  function deleteTodo(index) {
    todolista.update((todos) => {
      todos.splice(index, 1);
      return todos;
    });
  }
</script>

<h1>TO DO -Lista</h1>

{#if todos.length === 0}
  <p>Ei tehtäviä</p>
{:else}
  <ol>
    {#each todos as todo, index}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <li on:click={() => deleteTodo(index)}>{todo}</li>
    {/each}
  </ol>
{/if}

<style>
  li {
    margin: 15px;
  }
</style>
