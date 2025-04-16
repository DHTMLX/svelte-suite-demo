<script>
  import { onMount, onDestroy } from "svelte";
  import { Tree } from "@dhx/trial-suite";
  import { getData } from "../../data";
  
  let tree_container, tree;
  let { treeData } = getData();

  onMount(() => {
    tree = new Tree(tree_container, {
      data: treeData,
      checkbox: true,
      editable: true,
      keyNavigation: true,
      dragMode: "both"
    });

    return () => tree.destructor();
  });
  
  onDestroy(() => {
    tree?.destructor();
  });
</script>

<div bind:this={tree_container} class="container" />

<style>
  .container {
    flex-grow: 1;
  }
</style>
