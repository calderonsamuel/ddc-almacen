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

</script>

<div class="d-flex">
    <div class="flex-fill">
        <InputNumber label="N° de bolsa" bind:value={bolsa} disabled/>           
    </div>
    <div class="flex-fill">
        <InputNumber label="Peso recibido - kg" bind:value={peso_recibido} min={0} {disabled}/>           
    </div>
    <div class="flex-fill">
        <InputNumber label="Peso bruto -kg" bind:value={peso_bruto} min={0} {disabled}/>           
    </div>
    <div class="flex-fill">
        <InputText label="Observaciones" bind:value={observaciones} {disabled}/>
    </div>
    <div class="flex-fill">
        <InputNumber label="Peso modificado - kg" bind:value={peso_modificado} min={0} {disabled}/>
    </div>
    <div class="flex-fill align-self-center">
        {#if disabled}
            <InputButton className="btn-danger mb-3 ms-1" on:click><Icon name="trash"></Icon></InputButton>
        {:else}
            <InputButton className="btn-success mb-3 ms-1" on:click><Icon name="plus"></Icon></InputButton>
        {/if}
    </div>
</div>