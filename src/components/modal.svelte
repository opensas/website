<script lang="ts">
  import { createEventDispatcher } from "svelte";

  export let isOpen = false;
  export let title = "";

  const dispatch = createEventDispatcher();

  const closeModal = () => {
    dispatch("close");
  };

  const handleKeydown = (event: KeyboardEvent) => {
    if (event.key === "Escape") {
      closeModal();
    }
  };
</script>

<svelte:window on:keydown={handleKeydown} />

{#if isOpen}
  <div class="modal">
    <!-- TODO: Insert backdrop -->
    <div class="content text-blob">
      <div class="modal-header">
        <button aria-label="close this popup" on:click={closeModal}>
          <svg
            class="close"
            viewBox="0 0 14 14"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
            ><path
              d="M1 1l12 12m0-12L1 13"
              stroke="#12100C"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            /></svg
          >
        </button>
        <h2>{title}</h2>
      </div>
      <slot />
    </div>
  </div>
{/if}
