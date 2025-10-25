<script lang="ts">
  import { onMount } from 'svelte'
  import Home from './components/Home.svelte'
  import SwimmingDragon from './components/SwimmingDragon.svelte'
  import Timer from './components/Timer.svelte'
  import About from './components/About.svelte'
  
  type Page = 'home' | 'swimming-dragon' | 'timer' | 'about'
  
  let currentPage: Page = 'home'
  
  function navigate(page: Page): void {
    currentPage = page
  }
  
  onMount(() => {
    // Initialize Capacitor when the app loads
    if (typeof window !== 'undefined' && (window as any).Capacitor) {
      console.log('Capacitor is ready!')
    }
  })
</script>

<main>
  {#if currentPage === 'home'}
    <header>
      <h1>Tai Chi</h1>
    </header>
    <div class="content">
      <Home on:navigate={navigate} />
    </div>
  {:else}
    <header>
      <button class="back-button" on:click={() => navigate('home')}>
        ← Back to Home
      </button>
    </header>
    <div class="content">
      {#if currentPage === 'swimming-dragon'}
        <SwimmingDragon />
      {:else if currentPage === 'timer'}
        <Timer />
      {:else if currentPage === 'about'}
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
    background: #f5f1e8;
    min-height: 100vh;
  }
  
  main {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  
  header {
    background: rgba(245, 241, 232, 0.9);
    backdrop-filter: blur(10px);
    padding: 1rem 2rem;
    border-bottom: 2px solid #d4c4a8;
  }
  
h1 {
    color: #8b7355;
    margin: 0 0 1rem 0;
    font-size: 2.4rem;
    font-weight: 300;
    text-align: center;
    font-family: "Kasuga Brush W00 One";
  }
  
  .back-button {
    background: #d4c4a8;
    border: 2px solid #8b7355;
    color: #8b7355;
    padding: 0.5rem 1rem;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s ease;
  }
  
  .back-button:hover {
    background: #8b7355;
    color: #f5f1e8;
  }
  
  
  .content {
    flex: 1;
    padding: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  @media (max-width: 768px) {
    header {
      padding: 1rem;
    }
    
    h1 {
      font-size: 1.5rem;
    }
    
    .content {
      padding: 1rem;
    }
  }
</style>



