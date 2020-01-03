<script>
  import Icon from "./Icon.svelte";

  export let name = "";
  export let iconClassName = "";

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleClick() {
    dispatch("click", {});
  }
</script>

<style>
  button {
    margin: 0;
    padding: 0;
    border: none;
    outline: none;
    cursor: pointer;
    background: transparent;
  }

  button:focus,
  button:hover {
    opacity: 0.95;
  }

  button:active {
    opacity: 0.9;
  }
</style>

<button on:click={handleClick}>
  <Icon className={iconClassName} bind:name />
</button>
