<script lang="ts">
  import { onMount } from 'svelte'
  
  let greeting: string = 'Welcome to Tai Chi!'
  
  onMount(() => {
    // Add some dynamic content
    const hour: number = new Date().getHours()
    if (hour < 12) {
      greeting = 'Good Morning! Welcome to Tai Chi'
    } else if (hour < 18) {
      greeting = 'Good Afternoon! Welcome to Tai Chi'
    } else {
      greeting = 'Good Evening! Welcome to Tai Chi'
    }
  })
</script>

<div class="home-container">
  <div class="card">
    <h2>{greeting}</h2>
    <p>This is a modern Android app built with Svelte and Capacitor.</p>
    <div class="features">
      <div class="feature">
        <h3>🌱 Modern</h3>
        <p>Built with the latest web technologies</p>
      </div>
      <div class="feature">
        <h3>📱 Native</h3>
        <p>Runs as a native Android app</p>
      </div>
      <div class="feature">
        <h3>⚡ Fast</h3>
        <p>Optimized for performance</p>
      </div>
    </div>
    <button class="cta-button">
      Get Started
    </button>
  </div>
</div>

<style>
  .home-container {
    width: 100%;
    max-width: 600px;
  }
  
  .card {
    background: rgba(255, 255, 255, 0.95);
    border-radius: 20px;
    padding: 2rem;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(10px);
    text-align: center;
  }
  
  h2 {
    color: #333;
    margin: 0 0 1rem 0;
    font-size: 2rem;
    font-weight: 300;
  }
  
  p {
    color: #666;
    font-size: 1.1rem;
    line-height: 1.6;
    margin: 0 0 2rem 0;
  }
  
  .features {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1.5rem;
    margin: 2rem 0;
  }
  
  .feature {
    padding: 1rem;
    background: rgba(102, 126, 234, 0.1);
    border-radius: 15px;
    border: 1px solid rgba(102, 126, 234, 0.2);
  }
  
  .feature h3 {
    margin: 0 0 0.5rem 0;
    color: #667eea;
    font-size: 1.2rem;
  }
  
  .feature p {
    margin: 0;
    font-size: 0.9rem;
    color: #555;
  }
  
  .cta-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 1rem 2rem;
    border-radius: 25px;
    font-size: 1.1rem;
    cursor: pointer;
    transition: all 0.3s ease;
    margin-top: 1rem;
  }
  
  .cta-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 20px rgba(102, 126, 234, 0.3);
  }
  
  @media (max-width: 768px) {
    .card {
      padding: 1.5rem;
    }
    
    h2 {
      font-size: 1.5rem;
    }
    
    .features {
      grid-template-columns: 1fr;
      gap: 1rem;
    }
  }
</style>



