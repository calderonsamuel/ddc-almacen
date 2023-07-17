<script lang="ts">
    export let id = "";
    export let className = "btn-primary";
    
</script>

<button {id} type="button" class="btn {className}" on:click><slot></slot></button>