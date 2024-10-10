<script>
  import { Calendar, Timepicker } from "@dhx/trial-suite";
  import { onMount } from "svelte";

  let weekNode, timepickerNode, yearNode;

  onMount(() => {
    const week = new Calendar(weekNode, {
      weekStart: "monday",
      timePicker: true,
      range: true,
      value: [new Date(), new Date(Date.now() + 200000000)],
    });
    const timePicker = new Timepicker(timepickerNode, {
      controls: true,
      value: new Date(),
    });
    const year = new Calendar(yearNode, {
      timePicker: true,
      mode: "year",
      value: new Date(),
    });

    return () => {
      week.destructor();
      timePicker.destructor();
      year.destructor();
    };
  });
</script>

<div class="container-wrapper">
  <div class="container dhx_layout_calendar_cell" bind:this={weekNode}/>
  <div class="container dhx_layout_calendar_cell" bind:this={timepickerNode} />
  <div class="container dhx_layout_calendar_cell" bind:this={yearNode} />
</div>

<style>
  .container-wrapper {
    display: flex;
    height: fit-content;
    gap: 12px;
    justify-content: space-between;
  }
</style>
