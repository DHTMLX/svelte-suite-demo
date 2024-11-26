<script>
  import { Grid, Pagination } from "@dhx/trial-suite";
  let gNode, pNode, grid, paginator;
  import { onMount } from "svelte";
  import store from "../../store";

  onMount(() => {
    const gridConfig = {
      columns: [
        {
          gravity: 2,
          id: "time",
          header: [{ text: "Time", align: "center" }],
          type: "date",
          dateFormat: "%M %d, %H:%i",
        },
        { id: "nights", header: [{ text: "Nights" }] },
        {
          id: "price",
          header: [{ text: "Price" }],
          type: "number",
          numberMask: {
            groupSeparator: " ",
            prefix: "$",
          }
        },
        {
          gravity: 3,
          id: "contactPerson",
          header: [{ text: "Contact Person" }],
        },
        {
          gravity: 4,
          id: "contactEmail",
          header: [{ text: "Contact Email" }],
          htmlEnable: true,
          template: (text) => {
            return `<span class="contact_email";>${text}</span>`;
          },
        },
        {
          gravity: 2,
          id: "totalCost",
          header: [{ text: "Total Cost" }],
          type: "number",
          numberMask: {
            groupSeparator: " ",
            prefix: "$",
          }
        },
      ],
      autoWidth: true,
      css: "grid",
      multiselection: true,
      selection: "complex",
      editable: true,
    };
    // @ts-ignore
    grid = new Grid(gNode, gridConfig);

    paginator = new Pagination(pNode, {
      pageSize: 20,
      // @ts-ignore
      data: grid.data,
    });

    return () => {
      grid.destructor();
      paginator.destructor();
    };
  });

  $: grid?.data.parse($store.gridDataset);
</script>

<div class="container">
  <div bind:this={gNode} class="grid_container" />
  <div bind:this={pNode} />
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    border: var(--dhx-border);
    max-width: 800px;
  }
  .grid_container {
    min-height: 848px;
  }
</style>
