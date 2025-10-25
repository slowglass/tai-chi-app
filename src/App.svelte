<script lang="ts">
  import { onMount } from 'svelte'
  import { writable } from 'svelte/store'
  import Home from './components/Home.svelte'
  import SwimmingDragon from './components/SwimmingDragon.svelte'
  import Timer from './components/Timer.svelte'
  import About from './components/About.svelte'
  
  type Page = 'home' | 'swimming-dragon' | 'timer' | 'about'
  
  const currentPage = writable<Page>('home')
  
  function navigate(event: CustomEvent<Page>): void {
    const newPage = event.detail;
    currentPage.set(newPage);
    if (newPage !== 'home') {
      history.pushState({ page: newPage }, '', `#${newPage}`);
    } else {
      history.replaceState({ page: newPage }, '', '#'); // Replace state for home
    }
  }
  
  onMount(() => {
    // Initialize Capacitor when the app loads
    if (typeof window !== 'undefined' && (window as any).Capacitor) {
      console.log('Capacitor is ready!')
    }

    // Handle browser back/forward navigation
    const handlePopState = (event: PopStateEvent) => {
      if (event.state && event.state.page) {
        currentPage.set(event.state.page);
      } else {
        currentPage.set('home'); // Default to home if no state is found
      }
    };

    window.addEventListener('popstate', handlePopState);

    // Initial history state setup
    if (window.location.hash) {
      const initialPage = window.location.hash.substring(1) as Page;
      if (['swimming-dragon', 'timer', 'about'].includes(initialPage)) {
        currentPage.set(initialPage);
        history.replaceState({ page: initialPage }, '', window.location.hash);
      } else {
        currentPage.set('home');
        history.replaceState({ page: 'home' }, '', '#');
      }
    } else {
      history.replaceState({ page: 'home' }, '', '#');
    }

    return () => {
      window.removeEventListener('popstate', handlePopState);
    };
  })
</script>

<main>
  {#if $currentPage === 'home'}
    <header class="home-header">
      <h1 class="kasuga-brush-font">Tai Chi</h1>
    </header>
    <div class="content">
      <Home on:navigate={navigate} />
    </div>
  {:else}
    <header>
      <div style="flex-grow: 1; text-align: center;">
        {#if $currentPage === 'swimming-dragon'}
          <h1 class="kasuga-brush-font">Swimming Dragon</h1>
        {:else if $currentPage === 'timer'}
          <h1 class="kasuga-brush-font">Timer</h1>
        {:else if $currentPage === 'about'}
          <h1 class="kasuga-brush-font">About</h1>
        {/if}
      </div>
    </header>
    <div class="content">
      {#if $currentPage === 'swimming-dragon'}
        <SwimmingDragon />
      {:else if $currentPage === 'timer'}
        <Timer />
      {:else if $currentPage === 'about'}
        <About />
      {/if}
    </div>
  {/if}
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: #C9B177;
    min-height: 100vh;
  }
  
  main {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  
  header {
    background: #8C5A03;
    backdrop-filter: blur(10px);
    padding: 0.5rem 1rem;
    border-bottom: 2px solid #d4c4a8;
    display: flex; /* Make header a flex container */
    align-items: center; /* Vertically align items */
    justify-content: center; /* Center the single item */
  }

  .back-button:hover {
    background: #8b7355;
    color: #C9B117;
  }
  
  
  .content {
    flex: 1;
    padding: 0rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  

</style>



