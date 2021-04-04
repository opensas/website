<script context="module">
  export const prerender = true;
</script>

<script lang="ts">
  import CareerModal from "../components/careers/modal.svelte";
  import OpenGraph from "../components/open-graph.svelte";
  import { careers, perks } from "../contents/careers";

  let selectedCareer;
</script>

<OpenGraph
  data={{
    description: "Come join our fast-growing, venture-backed team.",
    title: "Careers at Gitpod",
    type: "website",
  }}
/>
<header>
  <h1>Always read to code.</h1>
  <p>Gitpod is a developers first company.</p>
  <a href="#openings">View {careers.length} openings</a>
</header>

<div>
  <!-- TODO: Insert cube monitor close-up image -->
</div>

<div>
  <h2>We want to make software engineering collaborative and joyful again.</h2>
  <p>
    We are a highly motivated, fully-remote team, organized in a flat hierarchy,
    and led by technical founders. We love open-source, have started and lead
    many popular open-source projects, and contribute to many others. In this
    fashion, we present at international conferences and collaborate openly
    around the globe.
  </p>
  <h2>Gitpod was founded for developers by developers</h2>
  <p>
    Everybody should have a frictionless experience with Gitpod, our product and
    our comany: no hurdles, no BS, no unnecessary extra steps.
  </p>
  <p>
    Developers architect our future. We are developers ourselves and built
    Gitpod to make lives of developers easier.
  </p>
</div>

<div>
  <h2>Perks And Recreation</h2>
  <ul>
    {#each perks as { title }}
      <li>{title}</li>
    {/each}
  </ul>
</div>

<div>
  <h2>Open positions</h2>
  <p>
    If there isn't an open position for you but you'd still want to work at
    Gitpod let us know via <a href="mailto:career@gitpod.io">career@gitpod.io</a
    >
  </p>
</div>

<div>
  <ul>
    {#each careers as career}
      <li>
        <button
          on:click={() => {
            selectedCareer = career;
          }}>{career.title}</button
        >
      </li>
    {/each}
  </ul>
</div>

<CareerModal career={selectedCareer} on:close={() => (selectedCareer = null)} />
