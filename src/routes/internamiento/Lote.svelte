<script lang="ts">
    import InputButton from "$lib/components/InputButton.svelte";
	import InputSelect from "$lib/components/InputSelect.svelte";
    import BolsaForm from "./BolsaForm.svelte";
    import { actaEstaIniciada } from "$lib/stores/acta";

    interface Bolsa {
        bolsa: number,
        peso_recibido: number,
        peso_bruto: number,
        observaciones: string,
        peso_modificado: number
    }
    interface Lote {
        numeroDeLote: number,
        tipoDeDroga: string,
        bolsas: Bolsa[]
    }

    let loteNumero = 1;
    let loteEstaIniciado = false;
    

    let loteActual: Lote;
    
    let bolsaActual: Bolsa;

    let tiposDeDroga = [
        {value: 0, label: "CC"},
        {value: 1, label: "CC mezcla"},
        {value: 2, label: "PBC"},
        {value: 3, label: "PBC mezcla"},
    ]

    let tipoDeDrogaSeleccionada = 0;

    const iniciarLote = () => {
        loteActual = {
            numeroDeLote: loteNumero,
            tipoDeDroga: tiposDeDroga.filter((x) => x.value === tipoDeDrogaSeleccionada)[0].label,
            bolsas: []
        };
        loteEstaIniciado = true;
    }
    
    const finalizarLote = () => {
        loteEstaIniciado = false;
        loteNumero = loteNumero + 1
    }
</script>

{#if $actaEstaIniciada}
    {#if loteEstaIniciado}
        <h3>Tipo de droga seleccionada: {loteActual.tipoDeDroga}</h3>
        <InputButton on:click={finalizarLote} className="btn-danger mb-3">Finalizar lote</InputButton>        
    {:else}
        <InputSelect label="Tipo de droga" options= {tiposDeDroga} bind:selected={tipoDeDrogaSeleccionada}/>
        <InputButton on:click={iniciarLote} className="btn-primary mb-3">Iniciar lote</InputButton>
    {/if}
{/if}
