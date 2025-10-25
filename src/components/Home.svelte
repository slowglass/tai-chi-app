<script lang="ts">
  import { createEventDispatcher } from 'svelte'
  import swimmingDragonIcon from '../assets/images/cards/K7.png'
  import timerIcon from '../assets/images/cards/K6.png'
  import aboutIcon from '../assets/images/cards/K12.png'
  import paperBackground from '../assets/images/cards/Paper.png'
  
  const dispatch = createEventDispatcher()
  
  interface Card {
    id: string
    title: string
    icon: string
    tint: string
    page: 'swimming-dragon' | 'timer' | 'about'
  }
  
  const cards: Card[] = [
    {
      id: 'swimming-dragon',
      title: 'Swimming Dragon',
      icon: swimmingDragonIcon,
      tint: 'brightness(0) saturate(100%) invert(27%) sepia(97%) saturate(7471%) hue-rotate(356deg)',
      page: 'swimming-dragon'
    },
    {
      id: 'timer',
      title: 'Timer',
      icon: timerIcon,
      tint: 'brightness(0) saturate(100%) invert(48%) sepia(98%) saturate(2476%) hue-rotate(86deg)',
      page: 'timer'
    },
    {
      id: 'about',
      title: 'About',
      icon: aboutIcon,
      tint: 'brightness(0) saturate(100%) invert(27%) sepia(98%) saturate(5969%) hue-rotate(211deg)',
      page: 'about'
    }
  ]
  
  function handleCardClick(page: string): void {
    dispatch('navigate', page)
  }
</script>

<div class="home-container">
  <div class="cards-grid">
    {#each cards as card}
      <div class="card" on:click={() => handleCardClick(card.page)} on:keydown={(e) => e.key === 'Enter' && handleCardClick(card.page)} role="button" tabindex="0">
        <div class="card-background"></div>
        <div class="card-content">
          <img src={card.icon} alt={card.title} class="card-icon" style="filter: {card.tint}" />
          <h3 class="card-title">{card.title}</h3>
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  .home-container {
    width: 100%;
    max-width: 500px;
    margin: 0 auto;
    padding: 2rem 1rem;
  }
  
  .cards-grid {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  
  .card {
    position: relative;
    background: url('../assets/images/cards/Paper.png') center/cover;
    border: 3px solid #8b7355;
    border-radius: 15px;
    padding: 2rem;
    cursor: pointer;
    transition: all 0.3s ease;
    min-height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 8px rgba(139, 115, 85, 0.2);
  }
  
  .card:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 16px rgba(139, 115, 85, 0.3);
    border-color: #6b5b47;
  }
  
  .card:active {
    transform: translateY(0);
  }
  
  .card-background {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: url('../assets/images/cards/Paper.png') center/cover;
    border-radius: 12px;
    opacity: 0.9;
  }
  
  .card-content {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .card-icon {
    width: 60px;
    height: 60px;
    margin-bottom: 1rem;
    transition: transform 0.3s ease;
  }
  
  .card:hover .card-icon {
    transform: scale(1.1);
  }
  
  .card-title {
    color: #8b7355;
    margin: 0;
    font-size: 1.3rem;
    font-weight: 500;
    text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.8);
  }
  
  @media (max-width: 768px) {
    .home-container {
      padding: 1rem;
    }
    
    .card {
      padding: 1.5rem;
      min-height: 100px;
    }
    
    .card-icon {
      width: 50px;
      height: 50px;
    }
    
    .card-title {
      font-size: 1.1rem;
    }
  }
</style>



