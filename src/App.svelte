<script>
  import { Router, Route } from "svelte-routing";

  import Main from "./views/Main.svelte";
  import TodoList from "./views/TodoList.svelte";
  import Search from "./components/Search.svelte";

  export let searchText = "";

  function handleInput(event) {
    searchText = event.detail.value;
  }

  export let list = [
    { id: 1, title: "A random todo item", completed: false },
    { id: 2, title: "Another random todo item", completed: true }
  ];

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
</script>

<Router>
  <Main>
    <Search on:input={handleInput} />
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
      <TodoList list={searchList(list, searchText)} on:itemClick={toggleItem} />
    </Route>
  </Main>
</Router>
