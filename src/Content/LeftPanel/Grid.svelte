<script>
  import { onMount, onDestroy } from "svelte";
  import { Grid, Pagination } from "@dhx/trial-suite";
  import { getData } from "../../data";

  let grid_container, pagination_container, grid, pagination;
  let { gridData } = getData();

  onMount(() => {
    const gridConfig = {
      data: gridData,
      autoWidth: true,
      columns: [
        {
          gravity: 2,
          id: "time",
          header: [{ text: "Time", align: "center" }],
          type: "date",
          dateFormat: "%M %d, %H:%i"
        },
        { id: "nights", header: [{ text: "Nights" }] },
        {
          id: "price",
          header: [{ text: "Price" }],
          type: "number",
          numberMask: {
            groupSeparator: " ",
            prefix: "$"
          }
        },
        {
          gravity: 3,
          id: "contactPerson",
          header: [{ text: "Contact Person" }]
        },
        {
          gravity: 4,
          id: "contactEmail",
          header: [{ text: "Contact Email" }],
          htmlEnable: true,
          template: (text) => {
            return `<span class="contact_email";>${text}</span>`;
          }
        },
        {
          gravity: 2,
          id: "totalCost",
          header: [{ text: "Total Cost" }],
          type: "number",
          numberMask: {
            groupSeparator: " ",
            prefix: "$"
          }
        }
      ],
      css: "grid",
      multiselection: true,
      selection: "complex",
      editable: true
    };

    // @ts-ignore
    grid = new Grid(grid_container, gridConfig);

    pagination = new Pagination(pagination_container, {
      pageSize: 20,
      // @ts-ignore
      data: grid.data
    });
  });

  onDestroy(() => {
    grid?.destructor();
    pagination?.destructor();
  });
</script>

<div class="grid_container-wrapper">
  <div bind:this={grid_container} class="grid_container" />
  <div bind:this={pagination_container} />
</div>
