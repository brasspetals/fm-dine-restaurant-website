<script>
  import { Router, Route } from "svelte-routing";
  import Home from "./components/pages/Home.svelte";
  import Book from "./components/pages/Book.svelte";

  export let url = "";
</script>

<Router url="{url}">
    <Route path="book" component="{Book}" />
    <Route path="/"><Home /></Route>
</Router>