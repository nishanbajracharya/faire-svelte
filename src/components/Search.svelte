<script>
  // Props
  export let className = "";
  export let containerClassName = "";

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleClick(event) {
    dispatch("input", {
      value: event.target.value
    });
  }
</script>

<style>
  .search-container {
    display: none;
  }
  .search-container {
    width: 100%;
    position: relative;
  }

  .search-bar {
    width: 100%;
    height: unset;
    font-size: 16px;
    min-height: 60px;
    background: #fff;
    line-height: 60px;
    border-radius: 3px;
    display: inline-block;
    box-sizing: border-box;
    vertical-align: middle;
    padding: 0 60px 0 20px;
    transition: 0.2s ease-in-out;
    border: 2px solid transparent;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.25);
  }

  .search-bar:focus {
    color: #49c;
    outline: none;
    background: #fff;
    border: 2px solid #49c;
  }

  @media (min-width: 30em) {
    .search-container {
      display: block;
    }
  }
</style>

<div class={`search-container ${containerClassName}`}>
  <input
    class={`search-bar ${className}`}
    placeholder="Search"
    on:input={handleClick} />
</div>
