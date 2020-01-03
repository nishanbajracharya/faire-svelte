<script>
  export let className = '';
  export let containerClassName = '';

  export let value = '';

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleChange(event) {
    value = event.target.value;
  }

  function handleKeyDown(event) {
    if (event.keyCode === 13) {
      dispatch('submit', { value })
      value = '';
    }
  }
</script>

<style>
  .input-bar {
    color: #49c;
    width: 100%;
    border: none;
    outline: none;
    padding: 0 20px;
    border-radius: 0;
    font-size: 16px;
    min-height: 60px;
    background: #fff;
    line-height: 60px;
    display: inline-block;
    box-sizing: border-box;
    vertical-align: middle;
    border-bottom: 1px solid #bababa;
  }

  .input-bar:focus {
    border-bottom: 1px solid #49c;
  }
</style>

<div class={`input-container ${containerClassName}`}>
  <input
    bind:value
    class={`input-bar ${className}`}
    placeholder="Add a task"
    on:change={handleChange}
    on:keydown={handleKeyDown}
    />
</div>