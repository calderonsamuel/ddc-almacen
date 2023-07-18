<script>
    import { base } from '$app/paths';
    import InputButton from "$lib/components/InputButton.svelte";
</script>

<div class="d-flex justify-content-center">
    <div style="max-width: 800px;">
        <h1>Bienvenido</h1>
        <p>Sistema de gestión del almacén de la Dirección de Control de Drogas y Cultivos Ilegales</p>
        <p>A continuación, elige el proceso que quieres iniciar</p>

        <div class="d-flex justify-content-center">
        <a href="{base}/internamiento"><InputButton>Internamiento</InputButton></a>
        <a href="{base}/destruccion" class="mx-2"><InputButton>Destrucción</InputButton></a>
        <a href="{base}/consultas"><InputButton>Consultas</InputButton></a>
        </div>
        
    </div>
</div>