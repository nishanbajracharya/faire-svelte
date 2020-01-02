<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleClick() {
    dispatch("click", {});
  }

  // Props
  export let label = "Button";
  export let className = "";
</script>

<style>
  .btn {
    margin: 0;
    border: none;
    outline: none;
    padding: 0 30px;
    line-height: 38px;
    text-align: center;
    border-radius: 3px;
    font-size: 0.875rem;
    text-decoration: none;
    box-sizing: border-box;
    vertical-align: middle;
    text-transform: uppercase;
  }
  .btn:not(:disabled) {
    cursor: pointer;
  }
  .btn-default {
    color: #333;
    border: 1px solid #ccc;
    background-color: #fff;
    box-shadow: 0 1px 2px hsla(0, 0%, 80%, 0.6);
    background-image: linear-gradient(#fff, #f2f2f2);
  }
  .btn-primary {
    color: #fff;
    border: 1px solid #49c;
    background-color: #49c;
    box-shadow: 0 1px 2px rgba(68, 153, 204, 0.6);
    background-image: linear-gradient(#49c, #358dc2);
  }
  .btn-default:focus, .btn-default:hover {
    color: #333;
    border: 1px solid #ccc;
    background-color: transparent;
    background-image: linear-gradient(#f2f2f2,#e6e6e6);
  }
  .btn-default:active {
    color: #333;
    border: 1px solid #ccc;
    background-color: transparent;
    background-image: linear-gradient(#d9d9d9,#e6e6e6);
  }
  .btn-primary:focus, .btn-primary:hover {
    color: #fff;
    border: 1px solid #49c;
    background-color: #358dc2;
    background-image: linear-gradient(#58a4d1,#49c);
  }
  .btn-primary:active {
    color: #fff;
    border: 1px solid #49c;
    background-color: #2f7eae;
    background-image: linear-gradient(#2f7eae,#358dc2);
  }
</style>

<button on:click={handleClick} class={`btn btn-default ${className}`}>
  {label}
</button>
