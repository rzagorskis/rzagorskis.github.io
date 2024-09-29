<script lang="ts">
  import { onMount } from 'svelte';
  import { marked } from 'marked';

  let postContent = '';

  async function fetchMarkdown() {
    const response = await fetch('./2024-09-29/first.md');
    const text = await response.text();
    postContent = await marked(text);
  }

  onMount(fetchMarkdown);
</script>

<div class="content" contenteditable="false" bind:innerHTML={postContent}></div>

<style>
  .content {
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-items: left;
    border: 1px solid red;
    padding: 2rem;
  }

  pre {
    background-color: gray;
  }
</style>
