<script lang="ts">
    import Acta from "./Acta.svelte";
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputText from "$lib/components/InputText.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import Icon from "$lib/components/Icon.svelte";

    let count = 0

    const addOne = () => {
        count = count + 1
    }
</script>

<div class="container-fluid">
    <div class="row">
        <div class="col-4 p-3 bg-secondary">
            <div class="row">
                <div class="col-6">
                    <Acta />
                </div>
                <div class="col-6">
                    <InputNumber id="lote" label="N° de lote" value={0} min={0}/>           
                </div>
            </div>
            <div class="row">
                <div class="col-6">
                    <InputNumber id="peso_recibido" label="Peso recibido - kg" value={0} min={0}/>           
                </div>
                <div class="col-6">
                    <InputNumber id="peso_bruto" label="Peso bruto -kg" value={0} min={0}/>           
                </div>
            </div>
            <InputText id="observaciones" label="Observaciones" />
            <div class="row">
                <div class="col-6">
                    <InputNumber id="peso_modificado" label="Peso modificado - kg" value={0} min={0}/>           
                </div>
                <div class="col-6">
                    <InputNumber id="bolsa" label="N° de bolsa" value={0} min={0}/>           
                </div>
            </div>
            <InputButton on:click={addOne}><Icon name="save"/>Save</InputButton>
        </div>
        <div class="col-8">
            {count}
        </div>
    </div>
</div>