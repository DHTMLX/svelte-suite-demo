<script>
  import MainContainer from "./MainCantainer/MainContainer.svelte";
  import Sidebar from "./Sidebar/Sidebar.svelte";
  import "@dhx/trial-suite/codebase/suite.min.css";
</script>

<main>
  <Sidebar />
  <MainContainer />
</main>

<style>
  main {
    height: 100%;
    width: 100%;
    display: flex;
  }
</style>
