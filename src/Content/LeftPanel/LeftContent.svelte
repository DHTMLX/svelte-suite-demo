<script>
  import Chart from "./Chart.svelte";
  import Calendars from "./Calendars.svelte";
  import Grid from "./Grid.svelte";
  import Ribbon from "./Ribbon.svelte";
  import SlidersLayout from "./SlidersLayout.svelte";
  import TicketsDataview from "./TicketsDataview.svelte";
  import Tree from "./Tree.svelte";
</script>

<div class="left_content_container-wrapper">
  <Grid />
  <Calendars />
  <Chart />
  <div class="left_content_block">
    <SlidersLayout />
    <Tree />
  </div>
  <Ribbon />
  <TicketsDataview />
</div>
