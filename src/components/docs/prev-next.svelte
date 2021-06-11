<script lang="ts">
  import type { MenuContext } from "../../routes/docs/menu";
  export let menuCtx: MenuContext;
</script>

<div class="flex justify-between">
  {#if menuCtx.prev}
    <a href={menuCtx.prev.path} title={`Prev: ${menuCtx.prev.title}`}> Prev </a>
  {:else}
    <div />
  {/if}
  {#if menuCtx.next}
    <a href={menuCtx.next.path} title={`Next: ${menuCtx.next.title}`}> Next </a>
  {:else}
    <div />
  {/if}
</div>
