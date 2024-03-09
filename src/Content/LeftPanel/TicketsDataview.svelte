<script>
  import { DataView } from "@dhx/trial-suite";
  import "@dhx/trial-suite/codebase/suite.min.css";
  import { onMount } from "svelte";
  import store from "../../store";
  let node, dataview;

  function template({ title, text, type, avatar, name, comments, time }) {
    return `
            <div class="dhx_dataview_template_a">
                <div class="dhx_dataview_template_a__head">
                    <div class="dhx_dataview_template_a__type dhx_dataview_template_a__type--${type}">${type}</div>
                    <div class="dhx_dataview_template_a__content">
                        <div class="dhx_dataview_template_a__title">${title}</div>
                        <div class="dhx_dataview_template_a__comment">${text}</div>
                    </div>
                </div>
                <div class="dhx_dataview_template_a__body">
                    <div class="dhx_dataview_template_a__person">
                        <div class="dhx_dataview_template_a__avatar" style="background-image: url(${avatar})"></div>
                        <div class="dhx_dataview_template_a__info">
                            <div class="dhx_dataview_template_a__time">${time}</div>
                            <div class="dhx_dataview_template_a__name">${name}</div>
                        </div>
                    </div>
                    <div class="dhx_dataview_template_a__comments">${comments}
                    <span class="mdi mdi-comment-outline"></span></div>
                </div>
            </div>
        `;
  }

  onMount(() => {
    dataview = new DataView(node, {
      template,
      itemsInRow: 2,
      css: "dhx_dataview_template_a_box",
    });

    return () => dataview.destructor();
  });
  $: dataview?.data.parse($store.ticketsDataviewData);
</script>

<div bind:this={node} />

<style>
</style>
