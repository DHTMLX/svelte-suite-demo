<script>
  import { onMount, onDestroy } from "svelte";
  import { Chart, Layout } from "@dhx/trial-suite";
  import { getData } from "../../data";

  let layout_container, layout, chart;
  let { seriesData, hotelsData } = getData();

  onMount(() => {
    layout = new Layout(layout_container, {
      type: "line",
      rows: [
        {
          header: "HOTELS",
          height: "500px",
          padding: 40,
          id: "chart",
          collapsable: true
        }
      ]
    });

    chart = new Chart(null, {
      data: hotelsData,
      type: "bar",
      scales: {
        bottom: {
          text: "month"
        },
        left: {
          maxTicks: 10,
          max: 100,
          min: 0
        }
      },
      // @ts-ignore
      series: seriesData,
      legend: {
        series: ["A", "B", "all"],
        halign: "right",
        valign: "top",
        itemPadding: 20,
        margin: 40
      }
    });

    layout.getCell("chart").attach(chart);
  });

  onDestroy(() => {
    layout?.destructor();
    chart?.destructor();
  });
</script>

<div bind:this={layout_container} class="container"></div>
