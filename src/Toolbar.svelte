<script>
  import { Toolbar, setTheme } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "./store";
  let node, toolbar;
  let contrast = false;
  let theme = "light";
  onMount(() => {
    toolbar = new Toolbar(node, {});
    toolbar.events.on("click", (id) => {
      switch (id) {
        case "theme": {
          const checked = !toolbar.data.getItem("theme").checked;
          toolbar.data.update("theme", {
            checked,
            icon: `mdi mdi-${
              !checked ? "weather-night" : "white-balance-sunny"
            }`,
          });
          theme = checked ? "dark" : "light";
          break;
        }
        case "contrast": {
          contrast = !contrast;
        }
      }
    });
    return () => toolbar.destructor();
  });

  $: toolbar?.data.parse($store.toolbarData);

  // @ts-ignore
  $: setTheme(`${contrast ? "contrast-" : ""}${theme}`);
</script>

<div bind:this={node} class="container"></div>

<style>
  .container {
    border-bottom: var(--dhx-border);
  }
</style>
