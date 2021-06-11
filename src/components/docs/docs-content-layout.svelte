<script>
  import BetaBanner from "./beta-banner.svelte";
  import OpenGraph from "../open-graph.svelte";
  import FeedbackWidget from "./feedback-widget.svelte";
  import EditInGitpod from "../../components/docs/edit-in-gitpod.svelte";
  import docsCurrentSectionStore from "../../stores/docs-current-section";
  import { page } from "$app/stores";
  import { getMenuContext } from "../../routes/docs/menu";
  import PrevNext from "./prev-next.svelte";

  const menuCtx = getMenuContext($page.path);
  export let section;
  export let title;

  $: $docsCurrentSectionStore = section;
</script>

<OpenGraph
  data={{
    description:
      "Explore the documentation to learn more about Gitpod.io and Gitpod Self-Hosted.",
    title: title ? title : "Gitpod Documentation",
  }}
/>
<div class="content-docs">
  <BetaBanner />
  <EditInGitpod />
  <slot />
  <FeedbackWidget />
  <PrevNext {menuCtx} />
</div>
