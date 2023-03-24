<script>
  import { onMount } from 'svelte';
  // import { writable } from 'svelte/store';

  // const advice = writable('');
  let advice = '';

  const fetchAdvice = async () => {
    const response = await fetch('https://api.adviceslip.com/advice');
    const data = await response.json();
    // advice.set(data.slip.advice);
    advice = data.slip.advice;
  };

  onMount(fetchAdvice);
</script>

<div class="api">
  <h3>Advice of the Day</h3>
  <!-- <p>{$advice}</p> -->
  <p>{advice}</p>
</div>

<style>
  p {
    font-style: oblique;
  }

  div.api {
    padding: 1.4em;
    font-size: 1.5em;
    background-color: rgb(255, 251, 237);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, 50%);
    border: 5px solid rgb(192, 232, 255);
  }
</style>
