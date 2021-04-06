<script lang="ts">
  import type { Career } from "../../types/career.type";
  import Modal from "../modal.svelte";

  export let career: Career;
</script>

<Modal isOpen={!!career} title={career.title} on:close>
  <p>{career.intro}</p>
  <p>{career.paragraphs}</p>

  {#each career.lists as list}
    <h3>{list.title}</h3>
    <ul>
      {#each list.items as item}
        <li>
          <p>
            <strong>{item.split(". ")[0]}</strong><br />
            {item.split(". ").slice(1, item.split(". ").length).join(". ")}
          </p>
        </li>
      {/each}
    </ul>
  {/each}
  <p>
    <a
      class="btn-conversion"
      href="mailto:career@gitpod.io?subject=Application as {career.title}"
      >Apply now</a
    >
  </p>
</Modal>
