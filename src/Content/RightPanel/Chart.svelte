<script>
  // @ts-nocheck

  import { Chart } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "../../store";
  let node, chart;

  onMount(() => {
    chart = new Chart(node, {
      type: "pie",
      series: [
        {
          value: "value",
          // monochrome: "#0288D1",
          color: "color",
          opacity: "opacity",
          text: "month",
          stroke: "var(--dhx-background-primary)",
          strokeWidth: 0,
        },
      ],
      legend: {
        values: {
          id: "value",
          text: "id",
          color: "color",
        },
        // monochrome: "#0288D1",
        align: "right",
        valign: "middle",
        width: 30,
      },
    });

    return () => chart.destructor();
  });
  $: chart?.data.parse($store.chartData);
</script>

<div bind:this={node} class="container" />
