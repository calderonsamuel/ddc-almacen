<script lang="ts">
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import { actaNumero, bolsaInicial, actaEstaIniciada } from "$lib/stores/acta";
	import { fade } from "svelte/transition";

    let acta: number;
    let bolsa: number;

    const fijarActa = () => {
        $actaNumero = `${acta}`.padStart(2, "0")
        $bolsaInicial = bolsa
        $actaEstaIniciada = true
    }
</script>

{#if !$actaEstaIniciada}
    <div transition:fade>
        <InputNumber id="acta" label="Indica el número de acta" bind:value={acta} min={0} floatingLabel={false}/>
        <InputNumber label="Indica el número de bolsa inicial" bind:value={bolsa} min={0} floatingLabel={false}/>
        <InputButton on:click={fijarActa}>Iniciar acta</InputButton>
    </div>
{:else}
    <h2>Acta de internamiento N° {$actaNumero}</h2>
{/if}
