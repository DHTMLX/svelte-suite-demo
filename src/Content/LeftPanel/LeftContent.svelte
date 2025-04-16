<script>
  import Chart from "./Chart.svelte";
  import Calendars from "./Calendars.svelte";
  import Grid from "./Grid.svelte";
  import Ribbon from "./Ribbon.svelte";
  import SlidersLayout from "./SlidersLayout.svelte";
  import TicketsDataview from "./TicketsDataview.svelte";
  import Tree from "./Tree.svelte";
</script>

<div class="container-wrapper">
  <Grid />
  <Calendars />
  <Chart />
  <div class="block">
    <SlidersLayout />
    <Tree />
  </div>
  <Ribbon />
  <TicketsDataview />
</div>

<style>
  .container-wrapper {
    display: flex;
    height: 100%;
    max-width: 800px;
    flex-grow: 1;
    gap: 12px;
    flex-direction: column;
  }
  .block {
    display: flex;
    gap: 12px;
    width: 100%;
    justify-content: space-between;
  }
</style>
