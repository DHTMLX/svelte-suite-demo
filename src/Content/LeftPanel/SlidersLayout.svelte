<script>
  import { onMount, onDestroy } from "svelte";
  import { Layout, Slider } from "@dhx/trial-suite";

  let layout_container, layout;

  function tickTemplate(value) {
    return `${value}`;
  }

  onMount(() => {
    const layout = new Layout(layout_container, {
      type: "none",
      height: "fit-content",
      cols: [
        {
          height: "content",
          align: "between",
          rows: [
            {
              padding: 10,
              height: "content",
              id: "slider1"
            },
            {
              padding: 10,
              height: "content",
              id: "slider2"
            },
            {
              padding: 10,
              height: "content",
              id: "slider3"
            },
            {
              padding: 10,
              height: "content",
              id: "slider4"
            }
          ]
        },
        {
          padding: "10px 20px",
          height: "260px",
          width: "20%",
          id: "slider5"
        }
      ]
    });

    const slider1 = new Slider(null, {
      min: 0,
      max: 40,
      step: 1
    });

    const slider2 = new Slider(null, {
      min: 0,
      max: 40,
      range: true,
      value: [10, 20],
      step: 1
    });

    const slider3 = new Slider(null, {
      min: 0,
      max: 40,
      step: 1,
      range: true,
      value: [0, 20],
      tick: 1,
      majorTick: 5,
      tickTemplate
    });

    const slider4 = new Slider(null, {
      min: 0,
      max: 40,
      step: 10,
      range: true,
      value: [0, 20]
    });

    const slider5 = new Slider(null, {
      mode: "vertical",
      range: true,
      min: 0,
      max: 40,
      step: 2,
      tick: 1,
      majorTick: 5,
      value: [0, 20],
      tickTemplate
    });

    // Attached all sliders in sliderLayout, which is main layout's cell
    layout.getCell("slider1").attach(slider1);
    layout.getCell("slider2").attach(slider2);
    layout.getCell("slider3").attach(slider3);
    layout.getCell("slider4").attach(slider4);
    layout.getCell("slider5").attach(slider5);
  });

  onDestroy(() => {
    layout?.destructor();
  });
</script>

<div bind:this={layout_container} class="sliders_container"></div>
