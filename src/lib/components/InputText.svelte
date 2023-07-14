<script lang="ts">
    export let id: string;
    export let label: string;
    export let value = "";
    export let placeholder = "";
    export let disabled = false;
    export let inputClass = "mb-3";

</script>

<div class="form-floating {inputClass}">
    <input type="text"
        class="form-control" 
        name={id} 
        {id} 
        bind:value={value}
        {placeholder}
        {disabled}
    >
    <label for={id} class="w-100">{label}</label>
</div>