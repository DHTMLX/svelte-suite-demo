<script>
  import { onMount, onDestroy } from "svelte";
  import { Sidebar } from "@dhx/trial-suite";
  import { getData } from "../data";

  let sidebar, sidebar_container;
  let { sidebarData } = getData();

  onMount(() => {
    sidebar = new Sidebar(sidebar_container, {
      data: sidebarData
    });

    sidebar.events.on("click", (id) => {
      if (id === "toggle") {
        const toggleItem = sidebar.data.getItem("toggle");
        sidebar.toggle();
        toggleItem.icon = sidebar.config.collapsed
          ? "mdi mdi-menu"
          : "mdi mdi-backburger";
      }
    });
  });

  onDestroy(() => {
    sidebar?.destructor();
  });
</script>

<div bind:this={sidebar_container} class="dhx_widget--border_right sidebar_container"></div>
