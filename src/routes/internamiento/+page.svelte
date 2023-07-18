<script lang="ts">
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputText from "$lib/components/InputText.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import Icon from "$lib/components/Icon.svelte";
	import { fade } from "svelte/transition";

    let acta: number;
    let bolsaInicial: number;
    let actaFijada: string;

    const fijarActa = () => {
        actaFijada = `${acta}`.padStart(2, "0")
    }

    interface Bolsa {
        bolsa: number,
        peso_recibido: number,
        peso_bruto: number,
        observaciones: string,
        peso_modificado: number
    }

    let lotes = [];
    let loteEstaIniciado: boolean;
    let loteActual:Bolsa[] = [];

    $: bolsa = bolsaInicial
    let peso_recibido, peso_bruto, observaciones, peso_modificado;

    const iniciarLote = () => {
        loteActual = []
    }

    const agregarBolsa = () => {
        let bolsaActual = {
            bolsa: bolsa,
            peso_recibido: peso_recibido,
            peso_bruto: peso_bruto,
            observaciones: observaciones,
            peso_modificado: peso_modificado
        }

        loteActual = [...loteActual, bolsaActual]

        bolsa = bolsa + 1
        peso_recibido = undefined
        peso_bruto = undefined
        observaciones = undefined
        peso_modificado = undefined
    }

    const eliminarBolsa = (bolsa: number) => {
        loteActual = loteActual.filter((x) => x.bolsa !== bolsa)
    }

</script>

<div class="d-flex justify-content-center">
    <div style="max-width: 800px;">
        {#if typeof actaFijada === "undefined"}
        <div out:fade>
            <InputNumber id="acta" label="Indica el número de acta" bind:value={acta} min={0} floatingLabel={false}/>
            <InputNumber label="Indica el número de bolsa inicial" bind:value={bolsaInicial} min={0} floatingLabel={false}/>
            <InputButton on:click={fijarActa}>Iniciar acta</InputButton>
        </div>
        {:else}
        <div in:fade>
            <h2>Acta de internamiento N° {actaFijada}</h2>
            <InputButton on:click={iniciarLote} className="btn-primary mb-3">Iniciar lote</InputButton>
            {#each loteActual as item}
                <div class="d-flex">
                    <div class="flex-fill">
                        <InputNumber label="N° de bolsa" disabled value={item.bolsa}/>           
                    </div>
                    <div class="flex-fill">
                        <InputNumber label="Peso recibido - kg" disabled value={item.peso_recibido}/>           
                    </div>
                    <div class="flex-fill">
                        <InputNumber label="Peso bruto -kg" disabled value={item.peso_bruto}/>           
                    </div>
                    <div class="flex-fill">
                        <InputText label="Observaciones" disabled value={item.observaciones}/>
                    </div>
                    <div class="flex-fill">
                        <InputNumber label="Peso modificado - kg" disabled value={item.peso_modificado}/>
                    </div>
                    <div class="flex-fill align-self-center">
                        <InputButton className="btn-danger mb-3 ms-1" on:click={() => eliminarBolsa(item.bolsa)}><Icon name="trash"></Icon></InputButton>
                    </div>
                </div>
            {/each}
            <div class="d-flex">
                <div class="flex-fill">
                    <InputNumber id="bolsa" label="N° de bolsa" bind:value={bolsa} disabled/>           
                </div>
                <div class="flex-fill">
                    <InputNumber id="peso_recibido" label="Peso recibido - kg" bind:value={peso_recibido} min={0}/>           
                </div>
                <div class="flex-fill">
                    <InputNumber id="peso_bruto" label="Peso bruto -kg" bind:value={peso_bruto} min={0}/>           
                </div>
                <div class="flex-fill">
                    <InputText id="observaciones" label="Observaciones" bind:value={observaciones}/>
                </div>
                <div class="flex-fill">
                    <InputNumber id="peso_modificado" label="Peso modificado - kg" bind:value={peso_modificado} min={0}/>
                </div>
                <div class="flex-fill align-self-center">
                    <InputButton className="btn-success mb-3 ms-1" on:click={agregarBolsa}><Icon name="plus"></Icon></InputButton>
                </div>
            </div>
        </div>
        {/if}
    </div>
</div>