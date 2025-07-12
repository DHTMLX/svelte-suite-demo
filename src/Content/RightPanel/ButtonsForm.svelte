<script>
  import { onMount, onDestroy } from "svelte";
  import { Form } from "@dhx/trial-suite";

  let buttons_form_container, form;

  onMount(() => {
    form = new Form(buttons_form_container, {
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
              size: "small"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Primary",
              color: "primary",
              full: true,
              view: "link",
              size: "small"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Primary",
              color: "primary",
              full: true,
              disabled: true,
              size: "small"
            }
          ]
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
              size: "small"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Secondary",
              color: "secondary",
              full: true,
              size: "small",
              view: "link"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Secondary",
              color: "secondary",
              full: true,
              size: "small",
              disabled: true
            }
          ]
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
              size: "small"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Danger",
              color: "danger",
              full: true,
              size: "small",
              view: "link"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Danger",
              color: "danger",
              full: true,
              size: "small",
              disabled: true
            }
          ]
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
              size: "small"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Success",
              color: "success",
              full: true,
              size: "small",
              view: "link"
            },
            {
              padding: 5,
              width: 140,
              type: "button",
              text: "Success",
              color: "success",
              full: true,
              size: "small",
              disabled: true
            }
          ]
        }
      ]
    });
  });

  onDestroy(() => {
    form?.destructor();
  });
</script>

<div bind:this={buttons_form_container} class="container" />
