<script>
  import { Router, Route } from "svelte-routing";
  import Home from "./components/pages/Home.svelte";
  import Book from "./components/pages/Book.svelte";

  export let url = "";
</script>

<Router url="{url}">
  <div class="container">
    <Route path="book" component="{Book}" />
    <Route path="/"><Home /></Route>
  </div>
</Router>

<style>
  .container {
	 overflow-x: hidden;
	 margin: 0 auto;
	 max-width: 93.75rem;
 }
</style>