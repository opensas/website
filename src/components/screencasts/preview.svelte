<script lang="ts">
  import type { Screencast } from "../../types/screencasts.type";
  import Logo from "../svgs/logo.svelte";

  export let screencast: Screencast;
  export let screencastNumber: number;

  $: screencastNumberPadded = `${screencastNumber}`.padStart(3, "0");
</script>

<style>
  a > div {
    padding: 16px 40% 16px 32px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.08),
      0px 5px 20px rgba(0, 0, 0, 0.12);
    border-radius: 12px;
    height: 225px;
    background-position: right center;
    display: flex;
    flex-flow: column;
    margin-bottom: 16px;
    &:hover,
    &:focus {
      position: relative;
    }
    &:hover::after,
    &:hover::before,
    &:focus::after,
    &:focus::before {
      content: "";
      position: absolute;
    }
    &:hover::after,
    &:focus::after {
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(18, 16, 12, 0.7);
      border-radius: inherit;
    }
    &:hover::before,
    &:focus::before {
      border: transparent solid;
      border-width: 20px 36px;
      border-left-color: white;
      z-index: 5;
      left: 45%;
      top: 45%;
    }
  }
  data {
    color: var(--light-grey);
  }
  h2 {
    flex: 1;
    margin: 0;
  }

  data,
  div a div {
    flex: 0;
  }

  a :global(svg) {
    width: 5.1rem;
  }
</style>

<a href="/screencasts/{screencast.title.toLowerCase().replace(/\s/g, '-')}">
  <div
    style="background-image: url(/images/screencasts/preview.jpg)"
    class="bg-no-repeat bg-auto text-left"
  >
    <data>Screencast {screencastNumberPadded}</data>
    <h2 class="text-large">{screencast.title}</h2>
    <!-- TODO: move css out of logo so we can change teh size -->
    <Logo />
  </div>
</a>
