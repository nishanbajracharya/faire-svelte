<script>
  import { Router, Route } from "svelte-routing";

  import Main from "./views/Main.svelte";
  import Button from "./components/Button.svelte";
</script>

<Router>
  <Main>
    <Route path="/about">
      <Button label="Add Todo" className="btn-primary" />
    </Route>
    <Route path="/">
      <Button label="Add Todo" />
      <Button label="Add Todo" className="btn-primary" />
    </Route>
  </Main>
</Router>
