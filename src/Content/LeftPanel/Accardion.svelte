<script>
  import { Chart, Layout } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "../../store";

  let node, accordion, chart;

  onMount(() => {
    accordion = new Layout(node, {
      type: "line",
      rows: [
        {
          header: "HOTELS",
          height: "500px",
          padding: 40,
          id: "chart",
          collapsable: true,
        },
      ],
    });
    chart = new Chart(null, {
      type: "bar",
      scales: {
        bottom: {
          text: "month",
        },
        left: {
          maxTicks: 10,
          max: 100,
          min: 0,
        },
      },
      series: [
        {
          id: "A",
          value: "Won deals",
          color: "none",
          fill: "var(--dhx-color-primary)",
          showText: true,
          showTextTemplate: (sum) => `$${sum}`,
        },
        {
          id: "B",
          value: "Lost deals",
          color: "none",
          fill: "var(--dhx-color-primary-light-active)",
          showText: true,
          showTextTemplate: (sum) => `$${sum}`,
        },
        {
          id: "all",
          value: "All deals",
          color: "none",
          fill: "var(--dhx-color-primary-disabled)",
          type: "area",
          strokeWidth: 0,
        },
      ],
      legend: {
        series: ["A", "B", "all"],
        halign: "right",
        valign: "top",
        itemPadding: 20,
        margin: 40,
      },
    });
    accordion.getCell("chart").attach(chart);
    return () => {
      accordion.destructor();
      chart.destructor();
    };
  });
  $: chart?.data.parse($store.hotelsData);
</script>

<div bind:this={node} class="container"></div>
