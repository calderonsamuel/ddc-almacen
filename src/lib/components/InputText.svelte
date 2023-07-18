<script lang="ts">
    export let id="";
    export let label: string;
    export let value = "";
    export let placeholder = "";
    export let disabled = false;
    export let inputClass = "mb-3";
    export let floatingLabel = true;

</script>

<!-- <div class="{floatingLabel? "form-floating":""} {inputClass}"> -->
<div class:form-floating={floatingLabel} class={inputClass}>
    {#if !floatingLabel}
        <label for={id} class="form-control">{label}</label>
    {/if}
    <input type="text"
        class="form-control" 
        name={id} 
        {id} 
        bind:value={value}
        {placeholder}
        {disabled}
    >
    {#if floatingLabel}
        <label for={id} class="w-100">{label}</label>
    {/if}
</div>