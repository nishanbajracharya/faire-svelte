<script>
  import { Router, Route } from "svelte-routing";

  import Main from "./views/Main.svelte";
  import Search from "./components/Search.svelte";

  export let searchText = "";

  function handleInput(event) {
    searchText = event.detail.value;
  }
</script>

<Router>
  <Main>
    <Search on:input={handleInput} />
    <Route path="/completed">Completed</Route>
    <Route path="/remaining">Remaining</Route>
    <Route path="/">Home</Route>
  </Main>
</Router>
