<script lang="ts">
  import { createEventDispatcher } from "svelte";

  export let isOpen = false;

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

<style>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: #ffc4c4;
  }
</style>

<svelte:window on:keydown={handleKeydown} />

{#if isOpen}
  <div class="modal">
    <!-- TODO: Insert backdrop -->
    <button on:click={closeModal}>x</button>
    <div class="content">
      <slot />
    </div>
  </div>
{/if}
