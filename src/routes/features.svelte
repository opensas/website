<script context="module">
  export const prerender = true;
</script>

<script>
  import Header from "../components/features/header.svelte";
  import Console from "../components/console.svelte";
  import OpenGraph from "../components/open-graph.svelte";
  import ScreencastPreview from "../components/screencasts/preview.svelte";
  import screencasts from "../contents/screencasts";
  import Workspaces from "../components/workspaces.svelte";
  import { terminalSource } from "../contents/terminal";

  const firstThreeScreencasts = screencasts.slice(0, 3);
</script>

<style lang="scss">
  article {
    margin-bottom: var(--x-large);
  }

  .double {
    margin-bottom: var(--x-large);
    flex-direction: column-reverse;

    @media (min-width: 50em) {
      flex-direction: initial;
    }

    .card {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .h4 {
      margin-top: 1rem;
    }

    a {
      display: block;
      margin-top: var(--micro);
      font-size: var(--p-large);
    }

    img {
      height: 223px;
    }
  }

  .triple {
    img {
      height: 90px;
    }

    h3 {
      min-height: 3rem;
    }

    p {
      margin: var(--xx-small) 0;
      font-size: var(--p-small);
      line-height: 150%;
    }
  }

  .triple a,
  .double a {
    /* TOD0: better contrast for AA */
    color: var(--brand-ripe);
  }

  .halfimages .text-large {
    margin: var(--x-small) 0;
  }

  .halfimages .prebuilds-p {
    margin-bottom: var(--x-large);

    @media (max-width: 768px) {
      margin-bottom: var(--x-small);
    }
  }

  .double .h4 {
    margin-bottom: var(--micro);
  }

  section h3:first-child,
  section h3:first-child + p {
    text-align: center;
  }

  .brief > img {
    width: 1100px;
    max-width: 90vw;
    margin: 2rem auto;
    box-shadow: var(--shadow-brand);
    border-radius: 0.875rem;
  }

  .brief > p {
    max-width: 900px;
    margin: auto;
  }

  .screencasts-container {
    margin-top: 0;
  }
</style>

<OpenGraph
  data={{
    description:
      "Learn about Gitpod's collaboration tools, workspace snapshots, supported programming languages, and much more.",
    title: "Features",
    type: "website",
  }}
/>

<Header />

<section class="halfimages">
  <article>
    <div>
      <Console source={terminalSource} />
    </div>
    <div>
      <h2 class="h4">Save Time with Prebuilds</h2>
      <p class="text-large prebuilds-p">
        Gitpod continuously builds your git branches like a CI server. This
        means no more waiting for dependencies to be downloaded and builds to
        finish.
      </p>
      <p>
        <a href="/docs/prebuilds/" class="btn-primary"
          >More about Prebuilt Workspaces</a
        >
      </p>
    </div>
  </article>

  <article>
    <div>
      <Workspaces />
    </div>
    <div>
      <h2 class="h4">Start Fresh with Ephemeral Dev Environments</h2>
      <p class="text-large">
        Dev environment as code assures you are always starting from a clean
        state and never gets dragged into long-living stateful environments. The
        end of all works-on-my-machine situations.
      </p>
      <p style="text-align: center">
        <a href="/blog/dev-env-as-code/" class="btn-secondary">
          More about Dev-Environments-as-Code</a
        >
      </p>
    </div>
  </article>
</section>

<section class="cards double">
  <div class="card">
    <img
      src="/images/features/features-3.svg"
      alt=""
      role="presentation"
      height="223"
      width="382"
    />
    <h2 class="h4">Collaboration with Workspace Sharing</h2>
    <p class="text-large">
      Collaborate with your friends, co-workers, and clients. Whenever you want
      to share a reproducible example of code or hunt down a bug together,
      simply take Snapshot.
    </p>

    <a href="/docs/sharing-and-collaboration/"> More about collaboration. </a>
  </div>
  <div class="card">
    <Console source={terminalSource} dark={true} shadow={false} narrow={true} />
    <h2 class="h4">Full linux machine <span>(incl sudo/docker)</span></h2>
    <p class="text-large">
      Instantly start a container in the cloud based on your Docker image.
      Install and configure tools easily.
    </p>

    <a href="https://www.youtube.com/watch?v=iYLCHQgj0fE" target="_blank"
      >Watch video to learn more</a
    >
  </div>
</section>

<section class="cards triple">
  <div class="card">
    <img
      src="/images/features/features-5.svg"
      alt=""
      role="presentation"
      height="90"
      width="185"
    />
    <h3 class="h5">Customize your workspace</h3>
    <p>
      Tweak your environment to suit your needs. From themes to extensions you
      have full control over it all.
    </p>
    <a href="/docs/vscode-extensions/">More about customization</a>
  </div>
  <div class="card">
    <img
      src="/images/features/features-6.svg"
      alt=""
      role="presentation"
      height="90"
      width="322"
    />
    <h3 class="h5">GitLab, GitHub, and Bitbucket Integration</h3>
    <p>
      Start your workflow from your Git hosting platform and let Gitpod beam you
      in a ready-to-code dev environment.
    </p>
    <a href="/docs/integrations/">More about Integrations</a>
  </div>
  <div class="card">
    <img
      src="/images/features/features-7.svg"
      alt=""
      role="presentation"
      height="90"
      width="130"
    />
    <h3 class="h5">Code Reviews Within the IDE</h3>
    <p>
      Open pull requests in Gitpod to run, navigate, and review the code. Reply
      to comments and publish code reviews right within Gitpod.
    </p>
    <a href="/blog/when-code-reviews-lgtm">More about Code Reviews</a>
  </div>
</section>

<section class="brief">
  <h2>VS Code and extensions in your browser</h2>
  <p class="text-large">
    Install any VS Code extension with one click via the integrated
    vendor-neutral marketplace Open VSX.
  </p>
  <img
    src="/images/features/gitpod-extensions.jpg"
    alt=""
    role="presentation"
    height="1110"
    width="748"
  />
</section>

<section class="brief screencasts-container">
  <h2>Get started with screencasts</h2>
  <div class="screencasts">
    {#each firstThreeScreencasts as screencast, index}
      <ScreencastPreview {screencast} screencastNumber={index + 1} />
    {/each}
  </div>
  <a href="/screencasts" class="btn-conversion">See all screencasts</a>
</section>
