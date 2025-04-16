<script>
  import { onMount, onDestroy } from "svelte";
  import { Tabbar } from "@dhx/trial-suite";

  let tabbar_container, tabbar;

  onMount(() => {
    tabbar = new Tabbar(tabbar_container, {
      tabAlign: "center",
      disabled: ["reports", "tickets", "users", "applications"],
      views: [
        { id: "dashboard", tab: "Dashboard" },
        { id: "reports", tab: "Reports" },
        { id: "tickets", tab: "Tickets" },
        { id: "users", tab: "Users" },
        { id: "applications", tab: "Applications" }
      ]
    });
  });

  onDestroy(() => {
    tabbar?.destructor();
  });
</script>

<div bind:this={tabbar_container}></div>
