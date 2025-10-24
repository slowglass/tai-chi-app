<script lang="ts">
  import { onMount } from 'svelte'
  import Home from './components/Home.svelte'
  import About from './components/About.svelte'
  
  type Page = 'home' | 'about'
  
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
  <header>
    <h1>Tai Chi</h1>
    <nav>
      <button 
        class:active={currentPage === 'home'} 
        on:click={() => navigate('home')}
      >
        Home
      </button>
      <button 
        class:active={currentPage === 'about'} 
        on:click={() => navigate('about')}
      >
        About
      </button>
    </nav>
  </header>
  
  <div class="content">
    {#if currentPage === 'home'}
      <Home />
    {:else if currentPage === 'about'}
      <About />
    {/if}
  </div>
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
  }
  
  main {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  
  header {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 1rem 2rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  }
  
  h1 {
    color: white;
    margin: 0 0 1rem 0;
    font-size: 2rem;
    font-weight: 300;
    text-align: center;
  }
  
  nav {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
  
  button {
    background: rgba(255, 255, 255, 0.2);
    border: 1px solid rgba(255, 255, 255, 0.3);
    color: white;
    padding: 0.5rem 1.5rem;
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-size: 1rem;
  }
  
  button:hover {
    background: rgba(255, 255, 255, 0.3);
    transform: translateY(-2px);
  }
  
  button.active {
    background: rgba(255, 255, 255, 0.4);
    border-color: rgba(255, 255, 255, 0.6);
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
    
    nav {
      flex-direction: column;
      align-items: center;
    }
    
    button {
      width: 200px;
    }
    
    .content {
      padding: 1rem;
    }
  }
</style>



