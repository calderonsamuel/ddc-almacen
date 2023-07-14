<script lang="ts">
    import { createEventDispatcher } from "svelte";

    export let id = "";
    export let className = "btn-primary";

    const dispath = createEventDispatcher()

    
</script>

<button {id} type="button" class="btn {className}">
    <slot></slot>
</button>