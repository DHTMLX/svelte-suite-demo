<script>
  // @ts-nocheck
  import { onMount, onDestroy } from "svelte";
  import { Chart } from "@dhx/trial-suite";
  import { getData } from "../../data";

  let chart_container, chart;
  let { chartData } = getData();

  onMount(() => {
    chart = new Chart(chart_container, {
      data: chartData,
      type: "pie",
      series: [
        {
          value: "value",
          // monochrome: "#0288D1",
          color: "color",
          opacity: "opacity",
          text: "month",
          stroke: "var(--dhx-background-primary)",
          strokeWidth: 0
        }
      ],
      legend: {
        values: {
          id: "value",
          text: "id",
          color: "color"
        },
        // monochrome: "#0288D1",
        align: "right",
        valign: "middle",
        width: 30
      }
    });
  });

  onDestroy(() => {
    chart?.destructor();
  });
</script>

<div bind:this={chart_container} class="container" />
