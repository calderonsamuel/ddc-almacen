<script lang="ts">
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import Icon from "$lib/components/Icon.svelte";
</script>

<div class="d-flex">
    <InputNumber id="acta" label="N° de acta" value={0} min={0} inputClass="flex-grow-1"/>
    <InputButton className="btn-primary ms-2 align-self-center flex-fill"><Icon name="pin-fill" className=""/></InputButton>

</div>
