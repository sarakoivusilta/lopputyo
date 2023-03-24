<script>
  import { onMount } from 'svelte';
  let date = new Date();
  $: time = date.toLocaleTimeString();
  onMount(() => {
    const timerId = setInterval(() => {
      date = new Date();
    }, 1000);
    return () => {
      clearInterval(timerId);
    };
  });
  //kellon toiminta otettu Stack Overflowsta, kun en ite saanu toimimaan omalla koodilla

  $: day = date.toLocaleDateString();
</script>

<div class="time">{time}</div>

<div class="day">
  <p>Tänään on {day}</p>
</div>

<style>
  div.time {
    color: rgb(0, 0, 0);
    padding-left: 3em;
    padding-top: 3.4em;
    font-size: 2em;
    display: flex;
    justify-content: left;
    flex-wrap: wrap;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS',
      sans-serif;
    font-weight: bold;
  }
  div.day {
    color: rgb(0, 0, 0);
    padding-top: 1em;
    padding-left: 1em;
    font-size: x-large;
    font-size: 1.8em;
    display: flex;
    justify-content: left;
    flex-wrap: wrap;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS',
      sans-serif;
    font-weight: 630;
  }
</style>
