<script>
  import { onMount, onDestroy } from "svelte";
  import { Calendar, Timepicker } from "@dhx/trial-suite";

  let week_container, timepicker_container, year_container, week, timepicker, year;

  onMount(() => {
    week = new Calendar(week_container, {
      weekStart: "monday",
      timePicker: true,
      range: true,
      value: [new Date(), new Date(Date.now() + 200000000)]
    });

    timepicker = new Timepicker(timepicker_container, {
      controls: true,
      value: new Date()
    });

    year = new Calendar(year_container, {
      timePicker: true,
      mode: "year",
      value: new Date()
    });
  });

  onDestroy(() => {
    week.destructor();
    timepicker.destructor();
    year.destructor();
  });
</script>

<div class="calendar_container-wrapper">
  <div class="container dhx_layout_calendar_cell" bind:this={week_container} />
  <div class="container dhx_layout_calendar_cell" bind:this={timepicker_container} />
  <div class="container dhx_layout_calendar_cell" bind:this={year_container} />
</div>
