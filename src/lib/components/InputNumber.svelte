<script lang="ts">
    export let id = "";
    export let label: string;
    export let value: number;
    export let min = -Infinity;
    export let max = Infinity;
    export let disabled = false;
    export let inputClass = "mb-3";
    export let floatingLabel = true;
</script>

<div class:form-floating={floatingLabel} class={inputClass}>
    {#if !floatingLabel}
        <label for={id}>{label}</label>
    {/if}
    <input
      type="number"
      class="form-control"
      {id}
      bind:value={value}
      {min}
      {max}
      {disabled}
    />
    {#if floatingLabel}
        <label for={id} class="w-100">{label}</label>
    {/if}
  </div>

<!-- <style>
    .form-floating>label {
        text-overflow: ellipsis;
    }
</style> -->