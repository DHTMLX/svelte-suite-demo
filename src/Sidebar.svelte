<script>
  import { Sidebar } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "./store";

  let sidebar, node;

  onMount(() => {
    sidebar = new Sidebar(node, {});
    sidebar.events.on("click", (id) => {
      if (id === "toggle") {
        const toggleItem = sidebar.data.getItem("toggle");
        sidebar.toggle();
        toggleItem.icon = sidebar.config.collapsed
          ? "mdi mdi-menu"
          : "mdi mdi-backburger";
      }
    });

    return () => sidebar.destructor();
  });

  $: sidebar?.data.parse($store.sidebarData)
</script>

<div bind:this={node} class="dhx_widget--border_right"></div>

<style>
  div {
    width: fit-content;
    height: 100%;
  }
</style>
