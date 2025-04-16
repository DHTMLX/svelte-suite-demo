<script>
  import Content from "../Content/Content.svelte";
  import Tabbar from "./Tabbar.svelte";
  import Toolbar from "./Toolbar.svelte";
</script>

<div class="container">
  <Toolbar />
  <Tabbar />
  <Content />
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    overflow: hidden;
  }
</style>
