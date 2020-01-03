<script>
import TodoItem from '../components/TodoItem.svelte';
import Container from '../components/Container.svelte';

export let list = [
  {title: 'A random todo item', completed: false},
  {title: 'Another random todo item', completed: true}
];

function toggleItem(index) {
  list[index].completed = !list[index].completed;
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
    {#each list as {title, completed}, i}
      <TodoItem bind:title bind:completed on:click={() => toggleItem(i)} />
    {/each}
  </div>
</Container>