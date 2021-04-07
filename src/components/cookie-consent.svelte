<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";

  $: showCookieConsent = false;

  const acceptCookies = () => {
    showCookieConsent = false;
    window.localStorage.setItem("cookie-consent", "true");
  };

  onMount(() => {
    showCookieConsent = !window.localStorage.getItem("cookie-consent");
  });
</script>

{#if showCookieConsent}
  <div
    out:fade
    class="fixed bottom-0 px-4 py-2 flex justify-between items-center w-full bg-sand-dark shadow-sm text-xs sm:text-sm md:text-base"
  >
    <p class="w-7/12 md:w-9/12">
      This website uses cookies to enhance the user experience. Read our <a
        href="/privacy">privacy policy</a
      > for more info.
    </p>
    <button
      on:click={acceptCookies}
      class="px-3 py-1 bg-off-white rounded-lg md:px-6 hover:bg-white"
      >Accept Cookies</button
    >
  </div>
{/if}
