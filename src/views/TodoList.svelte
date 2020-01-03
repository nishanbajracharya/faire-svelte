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

{#if list.length > 0}
  {#each list as { id, title, completed }}
    <TodoItem bind:title bind:completed on:click={() => handleClick(id)} />
  {/each}
{:else}
  <EmptyList />
{/if}
