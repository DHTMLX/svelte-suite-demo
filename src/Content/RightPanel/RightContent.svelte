<script>
  import ButtonsForm from "./ButtonsForm.svelte";
import Chart from "./Chart.svelte";
  import Colorpicker from "./Colorpicker.svelte";
  import Form from "./Form.svelte";
  import MessageDataview from "./MessageDataview.svelte";

</script>
<div class="wrapper">
    <Chart/>
    <Form />
    <ButtonsForm />
    <Colorpicker />
    <MessageDataview />
</div>

<style>
    .wrapper {
        display: flex;
        height: 100%;
        width: fit-content; 
        gap: 12px;
        flex: 1;
        flex-direction: column;       
    }
</style>