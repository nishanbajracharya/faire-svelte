<script>
  import uuid from 'uuid/v4';
  import { Router, Route } from "svelte-routing";

  import Main from "./views/Main.svelte";
  import Input from "./components/Input.svelte";
  import TodoList from "./views/TodoList.svelte";
  import Search from "./components/Search.svelte";
  import Container from "./components/Container.svelte";

  export let searchText = "";

  function handleInput(event) {
    searchText = event.detail.value;
  }

  export let list = [];

  function searchList(list = [], searchText = "") {
    return list.filter(item =>
      item.title.toLowerCase().includes(searchText.toLowerCase())
    );
  }

  function filterByCompleted(list = [], completed) {
    return list.filter(item => item.completed === completed);
  }

  function toggleItem(event) {
    const index = event.detail.index;

    const item = list.find(listItem => listItem.id === index);

    list[list.indexOf(item)].completed = !item.completed;
  }

  function addNewTodo(event) {
    list = list.concat({
      id: uuid(),
      title: event.detail.value,
      completed: false,
    });
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

<Router>
  <Main>
    <Search on:input={handleInput} />
    <Container>
      <div class="todo-list-container">
        <Input on:submit={addNewTodo}/>
        <Route path="/completed">
          <TodoList
            list={filterByCompleted(searchList(list, searchText), true)}
            on:itemClick={toggleItem} />
        </Route>
        <Route path="/remaining">
          <TodoList
            list={filterByCompleted(searchList(list, searchText), false)}
            on:itemClick={toggleItem} />
        </Route>
        <Route path="/">
          <TodoList
            list={searchList(list, searchText)}
            on:itemClick={toggleItem} />
        </Route>
      </div>
    </Container>
  </Main>
</Router>
