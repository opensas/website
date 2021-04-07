<script lang="ts" context="module">
  export async function load({ session }) {
    const posts = session.posts;
    return { props: { posts } };
  }
</script>

<script lang="ts">
  import type { BlogPost } from "../../types/blog-post.type";
  import OpenGraph from "../../components/open-graph.svelte";
  import PostPreview from "../../components/blog/post-preview.svelte";

  export let posts: BlogPost[];
</script>

<style>
  header,
  section {
    margin-top: var(--xx-large);
    text-align: center;
  }

  h2 {
    margin-bottom: var(--small);
  }
</style>

<OpenGraph
  data={{
    description:
      "Visit the Gitpod blog to learn about releases, tutorials, news and more.",
    title: "Blog",
    type: "website",
  }}
/>
<section>
  <h1>Blog</h1>
</section>
<div class="posts">
  {#each posts.slice(0, 6) as post}
    <PostPreview {post} isMostRecent />
  {/each}
</div>

<section>
  <h2>Previous posts</h2>
</section>
<div class="posts previous">
  {#each posts.slice(6) as post}
    <PostPreview {post} />
  {/each}
</div>
