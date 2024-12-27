<script lang="ts">
  import type { Article } from '../types';

  let articles: Article[] = [
    {
      id: 1,
      title: 'Introduction to Sveltes',
      content: 'Svelte is a modern JavaScript framework...',
    },
    {
      id: 2,
      title: 'Understanding something',
      content: "Reactivity is at the core of Svelte's design...",
    },
    {
      id: 3,
      title: 'Building Components',
      content: 'Components are the building blocks of Svelte apps...',
    },
    {
      id: 4,
      title: 'Introduction to Svelte',
      content: 'Svelte is a modern JavaScript framework...',
    },
    {
      id: 5,
      title: 'Understanding Reactivity',
      content: "Reactivity is at the core of Svelte's design...",
    },
    {
      id: 6,
      title: 'Building Components',
      content: 'Components are the building blocks of Svelte apps...',
    },
    {
      id: 7,
      title: 'Introduction to Svelte',
      content: 'Svelte is a modern JavaScript framework...',
    },
    {
      id: 8,
      title: 'Understanding Reactivity',
      content: "Reactivity is at the core of Svelte's design...",
    },
    {
      id: 9,
      title: 'Building Components',
      content: 'Components are the building blocks of Svelte apps...',
    },
  ];

  // Selected article state
  let selectedArticle: Article | null = null;

  // Function to handle article selection
  function selectArticle(article: Article): void {
    selectedArticle = article;
  }
</script>

<div class="container">
  <!-- Left: List View -->
  <ul class="list-view">
    {#each articles as article}
      <!-- svelte-ignore a11y_click_events_have_key_events -->
      <div
        role="button"
        tabindex="0"
        class="list-item ellipsis"
        on:click={() => selectArticle(article)}
      >
        {article.title}
      </div>
    {/each}
  </ul>

  <!-- Right: Preview View -->
  <div class="preview-view">
    {#if selectedArticle}
      <h2 class="text-red-600">{selectedArticle.title}</h2>
      <p>{selectedArticle.content}</p>
    {:else}
      <p class="placeholder">Select an article to preview its content.</p>
    {/if}
  </div>
</div>

<style>
  .container {
    display: flex;
    flex-direction: row;
    height: 100vh;
    font-family: Arial, sans-serif;
  }

  .list-view {
    flex: 0 0 20%;
    border-right: 1px solid #ccc;
    overflow-y: auto;
    background-color: #f9f9f9;
  }

  .list-item {
    padding: 0.2rem;
    cursor: pointer;
    transition: background-color 0.2s ease;
  }

  .list-item:hover {
    background-color: #e0e0e0;
  }

  .preview-view {
    flex: 1;
    padding: 1rem;
    overflow-y: auto;
  }

  .placeholder {
    color: #999;
    font-style: italic;
  }
</style>