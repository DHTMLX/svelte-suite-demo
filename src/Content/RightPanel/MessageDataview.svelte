<script>
  import { onMount, onDestroy } from "svelte";
  import { DataView } from "@dhx/trial-suite";
  import { getData } from "../../data";

  let dataview_container, dataview;
  let { messageDataviewData } = getData();

  function template({ mail, name, avatar, status, delivered }) {
    return `
        <div class="dhx_dataview_template_b">
            <div class="dhx_dataview_template_b__avatar" style="background-image: url(${avatar});">
                <div class="dhx_dataview_template_b__status dhx_dataview_template_b__status--${status}"></div>
            </div>
            <div class="dhx_dataview_template_b__title">Delivered ${delivered}</div>
            <div class="dhx_dataview_template_b__name">${name}</div>
            <a class="dhx_dataview_template_b__message" target="_blank" href="mailto:${mail}">
                <span class="dhx_dataview_template_b__message-icon mdi mdi-message-reply-text"></span>
                <span class="dhx_dataview_template_b__message-label">Message</span>
            </a>
        </div>
    `;
  }

  onMount(() => {
    dataview = new DataView(dataview_container, {
      data: messageDataviewData,
      template,
      itemsInRow: 2,
      css: "dhx_dataview_template_b_box"
    });
  });

  onDestroy(() => {
    dataview?.destructor();
  });
</script>

<div bind:this={dataview_container} />
