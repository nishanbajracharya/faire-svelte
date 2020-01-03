<script>
  import IconButton from "./IconButton.svelte";

  export let title = "";
  export let completed = false;

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleClick() {
    dispatch("click", {});
  }
</script>

<style>
  .todo-item {
    height: 60px;
    display: flex;
    padding: 0 20px;
    font-weight: 500;
    background: #fff;
    align-items: center;
    box-sizing: border-box;
    justify-content: space-between;
    border-bottom: 1px solid #c3c3c3;
  }

  .todo-item p {
    margin: 0;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    max-width: calc(100% - 40px);
  }

  .todo-item.completed p {
    color: #929292;
    text-decoration: line-through;
  }
</style>

<li class="todo-item" class:completed>
  <p>{title}</p>
  <IconButton
    name={completed ? 'check_circle' : 'radio_button_unchecked'}
    iconClassName={completed ? '' : 'blue'}
    on:click={handleClick} />
</li>
