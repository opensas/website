<script lang="ts">
  import { page } from "$app/stores";
  import { getMenuContext } from "../../routes/docs/menu";
  const menuCtx = getMenuContext($page.path);
</script>

<style lang="scss">
  a {
    @apply inline-flex border-b border-solid border-current transition duration-200;

    &:hover,
    &:focus {
      img {
        @apply opacity-100;
      }
    }
  }

  img {
    @apply opacity-60 transition duration-200;
  }
</style>

<div class="flex justify-between">
  {#if menuCtx.prev}
    <a href={menuCtx.prev.path} title={`Prev: ${menuCtx.prev.title}`}>
      <img
        src="/arrow-long.svg"
        alt="Arrow pointing backwards"
        class="transform rotate-180 mr-macro"
      /> Prev
    </a>
  {:else}
    <div />
  {/if}
  {#if menuCtx.next}
    <a href={menuCtx.next.path} title={`Next: ${menuCtx.next.title}`}>
      Next <img
        src="/arrow-long.svg"
        alt="Arrow pointing forwards"
        class="ml-macro"
      />
    </a>
  {:else}
    <div />
  {/if}
</div>
