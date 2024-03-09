<script>
  import LeftContent from "./LeftPanel/LeftContent.svelte";
  import RightContent from "./RightPanel/RightContent.svelte";

</script>
<div class="wrapper">
    <LeftContent />
    <RightContent />
</div>

<style>
    .wrapper {
        display: flex;
        flex-grow: 1;
        overflow: auto;
        padding: 12px;
        gap: 12px;
    }
    :global(.container) {
        border: var(--dhx-border);
    }
</style>