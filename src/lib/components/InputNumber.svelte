<script lang="ts">
    export let id: string;
    export let label: string;
    export let value: number;
    export let min = -Infinity;
    export let max = Infinity;
    export let inputClass = "mb-3";
    export let disabled = false;
</script>

<div class="form-floating {inputClass}">
    <input
      type="number"
      class="form-control"
      {id}
      bind:value={value}
      {min}
      {max}
      {disabled}
    />
    <label for={id} class="w-100">{label}</label>
  </div>

<!-- <style>
    .form-floating>label {
        text-overflow: ellipsis;
    }
</style> -->