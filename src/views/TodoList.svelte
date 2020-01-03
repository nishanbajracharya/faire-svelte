<script>
  import EmptyList from "./EmptyList.svelte";
  import TodoItem from "../components/TodoItem.svelte";
  import Container from "../components/Container.svelte";

  export let list = [];

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  // Event Handlers
  function handleClick(index) {
    dispatch("itemClick", { index });
  }
</script>

<style>
  .todo-list-container {
    background: #fff;
    overflow: hidden;
    border-radius: 3px;
    margin: 32px -20px 0;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.25);
  }
</style>

<Container>
  <div class="todo-list-container">
    {#if list.length > 0}
      {#each list as { id, title, completed }}
        <TodoItem bind:title bind:completed on:click={() => handleClick(id)} />
      {/each}
    {:else}
      <EmptyList />
    {/if}
  </div>
</Container>
