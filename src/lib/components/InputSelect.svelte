<script lang="ts">
    interface optionTypes {value: number, label: string}

    export let id = "";
    export let label = "";
    export let options: optionTypes[];
    export let selected = 0;

    
</script>

<div class="mb-3">
    <label for="{id}" class="mb-1">{label}</label>
    <select {id} class="form-select me-2" aria-label="Default select example" bind:value={selected}>
        {#each options as el}
            <option value={el.value}>{el.label}</option>
        {/each}
      </select>
</div>