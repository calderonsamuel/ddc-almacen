<script lang="ts">
    import InputNumber from "$lib/components/InputNumber.svelte";
    import InputText from "$lib/components/InputText.svelte";
    import InputButton from "$lib/components/InputButton.svelte";
    import Icon from "$lib/components/Icon.svelte";
	import { fade } from "svelte/transition";
	import Acta from "./Acta.svelte";
    import { actaNumero, bolsaInicial } from "$lib/stores/acta";
	import Lote from "./Lote.svelte";
	import BolsaForm from "./BolsaForm.svelte";

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

    $: bolsa = $bolsaInicial + loteActual.length;
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

        bolsa = $bolsaInicial + loteActual.length
        peso_recibido = undefined
        peso_bruto = undefined
        observaciones = undefined
        peso_modificado = undefined
    }

    const eliminarBolsa = (bolsa: number) => {
        loteActual = loteActual
            .filter((x) => x.bolsa !== bolsa)
            .map((x, i) => {
                x.bolsa = $bolsaInicial + i
                return x
            })
    }

</script>

<div class="d-flex justify-content-center">
    <div style="max-width: 800px;">
        <Acta/>
        <Lote />
        <!-- {#each loteActual as item}
            <BolsaForm 
                {...item}
                disabled
                on:click={() => eliminarBolsa(item.bolsa)}
            />
        {/each}
        <BolsaForm 
            bind:bolsa={bolsa}
            bind:peso_recibido={peso_recibido}
            bind:peso_bruto={peso_bruto}
            bind:observaciones={observaciones}
            bind:peso_modificado={peso_modificado}
            on:click={agregarBolsa} 
        /> -->
    </div>
</div>