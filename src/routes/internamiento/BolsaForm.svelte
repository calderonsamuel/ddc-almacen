<script lang="ts">
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputText from "$lib/components/InputText.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import Icon from "$lib/components/Icon.svelte";

    export let bolsa: number;
    export let peso_recibido: number;
    export let peso_bruto: number;
    export let observaciones: string;
    export let peso_modificado: number;
    export let disabled = false;

    $: btn_color = disabled ? "btn-danger" : "btn-success"
    $: iconName = disabled ? "trash" : "plus"
    $: inputClass = disabled ? "mb-1" : "mb-3"

</script>

<div class="d-flex">
    <div class="flex-shrink-1">
        <InputNumber label="N° de bolsa" bind:value={bolsa} disabled {inputClass}/>           
    </div>
    <div class="">
        <InputNumber label="Peso recibido - kg" bind:value={peso_recibido} min={0} {disabled} {inputClass}/>           
    </div>
    <div class="">
        <InputNumber label="Peso bruto -kg" bind:value={peso_bruto} min={0} {disabled} {inputClass}/>           
    </div>
    <div class="flex-grow-1">
        <InputText label="Observaciones" bind:value={observaciones} {disabled} {inputClass}/>
    </div>
    <div class="">
        <InputNumber label="Peso modificado - kg" bind:value={peso_modificado} min={0} {disabled} {inputClass}/>
    </div>
    <div class="flex-shrink-1 align-self-center">
        <InputButton className="{btn_color} mb-3 ms-1" on:click><Icon name={iconName}></Icon></InputButton>
    </div>
</div>