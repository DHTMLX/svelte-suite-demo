<script>
  import { Layout, Slider } from "@dhx/trial-suite";
  import { onMount } from "svelte";

  let node;

  function tickTemplate(value) {
    return `${value}`;
  }

  onMount(() => {
    const sliderLayout = new Layout(node, {
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
              id: "slider1",
            },
            {
              padding: 10,
              height: "content",
              id: "slider2",
            },
            {
              padding: 10,
              height: "content",
              id: "slider3",
            },
            {
              padding: 10,
              height: "content",
              id: "slider4",
            },
          ],
        },
        {
          padding: "10px 20px",
          height: "260px",
          width: "20%",
          id: "slider5",
        },
      ],
    });

    const slider1 = new Slider(null, {
      min: 0,
      max: 40,
      step: 1,
    });

    // Slider 2 initialization
    const slider2 = new Slider(null, {
      min: 0,
      max: 40,
      range: true,
      value: [10, 20],
      step: 1,
    });

    // Slider 3 initialization
    const slider3 = new Slider(null, {
      min: 0,
      max: 40,
      step: 1,
      range: true,
      value: [0, 20],
      tick: 1,
      majorTick: 5,
      tickTemplate,
    });

    // Slider 4 initialization
    const slider4 = new Slider(null, {
      min: 0,
      max: 40,
      step: 10,
      range: true,
      value: [0, 20],
    });

    // Slider 5 initialization
    const slider5 = new Slider(null, {
      mode: "vertical",
      range: true,
      min: 0,
      max: 40,
      step: 2,
      tick: 1,
      majorTick: 5,
      value: [0, 20],
      tickTemplate,
    });

    // Attached all sliders in sliderLayout, which is main layout's cell
    sliderLayout.getCell("slider1").attach(slider1);
    sliderLayout.getCell("slider2").attach(slider2);
    sliderLayout.getCell("slider3").attach(slider3);
    sliderLayout.getCell("slider4").attach(slider4);
    sliderLayout.getCell("slider5").attach(slider5);
    return sliderLayout.destructor;
  });
</script>

<div bind:this={node} class="container"></div>

<style>
  .container {
    flex-grow: 1;
  }
</style>
