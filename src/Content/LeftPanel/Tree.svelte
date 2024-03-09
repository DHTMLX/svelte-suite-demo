<script>
  import { Tree } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  import store from "../../store";
  let node, tree;

  onMount(() => {
    tree = new Tree(node, {
      checkbox: true,
      editable: true,
      keyNavigation: true,
      dragMode: "both",
    });

    return () => tree.destructor();
  });
  $: tree?.data.parse($store.treeData);
</script>

<div bind:this={node} class="container" />

<style>
  .container {
    flex-grow: 1;
  }
</style>
