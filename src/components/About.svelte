<script lang="ts">
  interface TechItem {
    name: string
    description: string
    icon: string
  }
  
  const techStack: TechItem[] = [
    { name: 'Svelte', description: 'Modern reactive framework', icon: '⚡' },
    { name: 'Capacitor', description: 'Cross-platform native runtime', icon: '📱' },
    { name: 'Vite', description: 'Fast build tool', icon: '🚀' },
    { name: 'GitHub Actions', description: 'Automated CI/CD', icon: '🔄' }
  ]
</script>

<div class="about-container">
  <div class="card">
    <h2>About This App</h2>
    <p>This Android application demonstrates modern web-to-native development using cutting-edge technologies.</p>
    
    <div class="tech-section">
      <h3>Technology Stack</h3>
      <div class="tech-grid">
        {#each techStack as tech}
          <div class="tech-item">
            <div class="tech-icon">{tech.icon}</div>
            <h4>{tech.name}</h4>
            <p>{tech.description}</p>
          </div>
        {/each}
      </div>
    </div>
    
    <div class="info-section">
      <h3>Key Features</h3>
      <ul>
        <li>✅ Built with modern web technologies</li>
        <li>✅ Native Android performance</li>
        <li>✅ Automated builds with GitHub Actions</li>
        <li>✅ Responsive design</li>
        <li>✅ Easy to maintain and extend</li>
      </ul>
    </div>
    
    <div class="version-info">
      <p><strong>Version:</strong> 0.0.1</p>
      <p><strong>Build:</strong> Capacitor + Svelte</p>
    </div>
  </div>
</div>

<style>
  .about-container {
    width: 100%;
    max-width: 700px;
  }
  
  .card {
    background: rgba(255, 255, 255, 0.95);
    border-radius: 20px;
    padding: 2rem;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(10px);
  }
  
  h2 {
    color: #333;
    margin: 0 0 1rem 0;
    font-size: 2rem;
    font-weight: 300;
    text-align: center;
  }
  
  p {
    color: #666;
    font-size: 1.1rem;
    line-height: 1.6;
    margin: 0 0 2rem 0;
  }
  
  .tech-section, .info-section {
    margin: 2rem 0;
  }
  
  h3 {
    color: #667eea;
    margin: 0 0 1rem 0;
    font-size: 1.3rem;
    font-weight: 400;
  }
  
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }
  
  .tech-item {
    background: rgba(102, 126, 234, 0.1);
    border-radius: 15px;
    padding: 1.5rem;
    text-align: center;
    border: 1px solid rgba(102, 126, 234, 0.2);
  }
  
  .tech-icon {
    font-size: 2rem;
    margin-bottom: 0.5rem;
  }
  
  .tech-item h4 {
    margin: 0 0 0.5rem 0;
    color: #667eea;
    font-size: 1.1rem;
  }
  
  .tech-item p {
    margin: 0;
    font-size: 0.9rem;
    color: #555;
  }
  
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    padding: 0.5rem 0;
    color: #666;
    font-size: 1rem;
  }
  
  .version-info {
    background: rgba(102, 126, 234, 0.1);
    border-radius: 15px;
    padding: 1rem;
    margin-top: 2rem;
    text-align: center;
  }
  
  .version-info p {
    margin: 0.5rem 0;
    font-size: 0.9rem;
  }
  
  @media (max-width: 768px) {
    .card {
      padding: 1.5rem;
    }
    
    h2 {
      font-size: 1.5rem;
    }
    
    .tech-grid {
      grid-template-columns: 1fr;
    }
  }
</style>



