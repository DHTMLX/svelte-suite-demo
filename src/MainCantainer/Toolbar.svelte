<script>
  import { onMount, onDestroy } from "svelte";
  import { Toolbar, setTheme } from "@dhx/trial-suite";
  import { getData } from "../data";

  let toolbar, toolbar_container;
  let contrast = false;
  let theme = "light";
  let { toolbarData } = getData();

  onMount(() => {
    toolbar = new Toolbar(toolbar_container, {
      data: toolbarData
    });

    toolbar.events.on("click", (id) => {
      switch (id) {
        case "theme": {
          const checked = !toolbar.data.getItem("theme").checked;
          toolbar.data.update("theme", {
            checked,
            icon: `mdi mdi-${
                    !checked ? "weather-night" : "white-balance-sunny"
                  }`
          });
          theme = checked ? "dark" : "light";
          break;
        }
        case "contrast": {
          contrast = !contrast;
        }
      }
    });
  });

  onDestroy(() => {
    toolbar?.destructor();
  });

  // @ts-ignore
  $: setTheme(`${contrast ? "contrast-" : ""}${theme}`);
</script>

<div bind:this={toolbar_container} class="toolbar_container"></div>
