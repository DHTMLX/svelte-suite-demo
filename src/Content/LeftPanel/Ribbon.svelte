<script>
  import { Ribbon } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "../../store";
  let node, ribbon;

  onMount(() => {
    ribbon = new Ribbon(node, {
      css: "dhx_widget--bordered",
    });

    return () => ribbon.destructor();
  });
  $: ribbon?.data.parse($store.ribbonData);
</script>

<div bind:this={node} class="container" />

<style>
  .container {
    padding: 50px;
    background: var(--dhx-background-primary);
  }
</style>
