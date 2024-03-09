<script>
  import { Tabbar } from "@dhx/trial-suite";
  import { onMount } from "svelte";

  let node, tabbar;

  onMount(() => {
    tabbar = new Tabbar(node, {
      tabAlign: "center",
      disabled: ["reports", "tickets", "users", "applications"],
      views: [
        { id: "dashboard", tab: "Dashboard" },
        { id: "reports", tab: "Reports" },
        { id: "tickets", tab: "Tickets" },
        { id: "users", tab: "Users" },
        { id: "applications", tab: "Applications" },
      ],
    });

    return tabbar.destructor;
  });
</script>

<div bind:this={node}></div>
