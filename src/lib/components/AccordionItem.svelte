<script lang="ts">
    export let parentId: string;
    export let itemId: string;
    export let expanded = false;

    let classes = {
        btn: expanded ? "":"collapsed",
        content: expanded ? "collapse show":"collapse"
    }
</script>

<div class="accordion-item">
    <h2 class="accordion-header" id="{itemId}-header">
      <button class="accordion-button {classes.btn}" type="button" data-bs-toggle="collapse" data-bs-target="#{itemId}" aria-expanded={expanded} aria-controls="{itemId}">
        <slot name= "header">
            Item's header
        </slot>
    </button>
</h2>
<div id="{itemId}" class="accordion-collapse {classes.content}" data-bs-parent="#{parentId}" aria-labelledby="{itemId}-header">
    <div class="accordion-body">
        <slot name= "body">
            Item's body
        </slot>
      </div>
    </div>
  </div>

  <style>
    .accordion-body {
        background-color: #f8ffff;
    }

    /* .accordion-button {
        background-color: aqua;
    }

    .accordion-button:active {
        background-color: aquamarine;
    } */
  </style>