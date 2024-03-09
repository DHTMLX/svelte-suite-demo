<script>
  import { Form } from "@dhx/trial-suite";
  import { onMount } from "svelte";
  let node, form;

  onMount(() => {
    form = new Form(node, {
      height: "content",
      padding: 40,
      align: "between",
      rows: [
        {
          align: "between",
          cols: [
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Primary",
              color: "primary",
              icon: "dxi dxi-plus",
              full: true,
              size: "small",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Primary",
              color: "primary",
              full: true,
              view: "link",
              size: "small",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Primary",
              color: "primary",
              full: true,
              disabled: true,
              size: "small",
            },
          ],
        },
        {
          align: "between",
          cols: [
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Secondary",
              color: "secondary",
              icon: "dxi dxi-plus",
              full: true,
              size: "small",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Secondary",
              color: "secondary",
              full: true,
              size: "small",
              view: "link",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Secondary",
              color: "secondary",
              full: true,
              size: "small",
              disabled: true,
            },
          ],
        },
        {
          align: "between",
          cols: [
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Danger",
              color: "danger",
              icon: "dxi dxi-plus",
              full: true,
              size: "small",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Danger",
              color: "danger",
              full: true,
              size: "small",
              view: "link",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Danger",
              color: "danger",
              full: true,
              size: "small",
              disabled: true,
            },
          ],
        },
        {
          align: "between",
          cols: [
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Success",
              color: "success",
              icon: "dxi dxi-plus",
              full: true,
              size: "small",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Success",
              color: "success",
              full: true,
              size: "small",
              view: "link",
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Success",
              color: "success",
              full: true,
              size: "small",
              disabled: true,
            },
          ],
        },
      ],
    });

    return () => form.destructor();
  });
</script>

<div bind:this={node} class="container" />
