<script>
  import { onMount, onDestroy } from "svelte";
  import { Ribbon } from "@dhx/trial-suite";
  import { getData } from "../../data";

  let ribbon_container, ribbon;
  const { ribbonData } = getData();

  onMount(() => {
    ribbon = new Ribbon(ribbon_container, {
      data: ribbonData,
      css: "dhx_widget--bordered"
    });
  });

  onDestroy(() => {
    ribbon?.destructor();
  });
</script>

<div bind:this={ribbon_container} class="ribbon_container" />
