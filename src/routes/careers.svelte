<script context="module">
  export const prerender = true;
</script>

<script lang="ts">
  import CareerModal from "../components/careers/modal.svelte";
  import OpenGraph from "../components/open-graph.svelte";
  import { careers, perks } from "../contents/careers";

  let selectedCareer;
</script>

<style lang="scss">
  .heroImage {
    margin: 0 auto 2rem;
  }

  p {
    font-size: var(--p-large);
    line-height: 133.33%;
  }

  header {
    margin-bottom: var(--x-small);
    h1 {
      margin-bottom: var(--micro);
    }
  }

  section {
    width: 50rem;
    max-width: 96vw;
    margin: auto;
  }

  section h2 {
    margin: var(--x-large) 0 var(--xx-small);
  }

  section p,
  section h2 {
    padding-left: 2rem;
  }

  article {
    p + p {
      margin-top: var(--x-small);
    }
  }

  .openings {
    margin: var(--xx-large) 0;
  }
</style>

<OpenGraph
  data={{
    description: "Come join our fast-growing, venture-backed team.",
    title: "Careers at Gitpod",
    type: "website",
  }}
/>
<header>
  <h1>Always ready to code.</h1>
  <p>Gitpod is a developers first company.</p>
  <p>
    <a href="#jobs" class="btn-conversion">View {careers.length} openings</a>
  </p>
</header>

<img
  src="/images/careers/careers-hero.png"
  alt=""
  role="presentation"
  width="1136"
  height="631"
  class="heroImage"
/>

<section>
  <article class="hilited">
    <h2 class="h4">
      Make software engineering collaborative and joyful again.
    </h2>
    <p>
      Developers write software within languages/frameworks, build tools, glue
      them together to (tool) chains, develop against APIs and communicate and
      collaborate with our colleagues. All of that should be efficient, joyful
      and secure.
    </p>
    <p>
      Yet it is not. Devs constantly struggle with larger codebases, cluttered
      dependencies, security policies and unnecessary friction in their
      workflows.
    </p>
    <p>
      We want to make developers feel again that everything is at their
      fingertips.
    </p>

    <h2 class="h4">
      Gitpod was founded because we were frustrated by manually setting up and
      maintaining dev environments.
    </h2>
    <p>
      We are building Gitpod in the open to easily spin-up fresh dev
      environments for any task. Those ephemeral environments are fast &
      powerful, fully automated & initialized. They empower developers to
      immediately start coding, debugging, and testing their code.
    </p>
    <p>Only then developers are always ready-to-code.</p>

    <h2 class="h4">
      The company was founded in 2020 and today over 350,000 devs gitpodified
      their workflows.
    </h2>
    <p>
      We are greateful to be backed by some of the best venture firms and
      advisors of the world. We recently announced a 13m funding round.
    </p>

    <p>
      Come join a quickly growing venture-backed team and work together with
      incredible humans from four continents 🌍
    </p>

    <p>
      We are open minded, transparent and curious. We remain students of the
      game, not masters of the game.We aim for a frictionless experience when
      interacting with our product, our company and our brand: no hurdles, no
      BS, no unnecessary extra steps.
    </p>

    <p>
      We are fully-distributed. You can work from anywhere and schedule your
      working hours the way it fits best for you. We make sure you are all set
      and will treat you well.We are not as diverse as we would like to be.
    </p>

    <p>
      Help us to change that and shape Gitpod’s future from anywhere in the
      world! 🌈 🌍
    </p>
  </article>

  <h2 class="h4">What we offer</h2>
  <ul class="perks">
    {#each perks as { title, emoji }}
      <li class="text-medium"><span class="emoji">{emoji}</span>{title}</li>
    {/each}
  </ul>

  <div class="openings">
    <h2 id="jobs" class="h4">Open positions</h2>
    <p>
      If there isn't an open position for you but you'd still want to work at
      Gitpod let us know via <a href="mailto:career@gitpod.io"
        >career@gitpod.io</a
      >
    </p>

    <div>
      <ul class="jobs">
        {#each careers as career}
          <li id={career.title.toLowerCase().replace(/\s/g, "-")}>
            <button
              on:click={() => {
                selectedCareer = career;
              }}>{career.title}</button
            >
          </li>
        {/each}
      </ul>
    </div>
  </div>

  <CareerModal
    career={selectedCareer}
    on:close={() => (selectedCareer = null)}
  />
</section>
