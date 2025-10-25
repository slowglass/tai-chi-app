<script lang="ts">
  // No imports needed for the SVG
</script>

<div class="page-container">
    <div class="yin-yang" style="animation-name: yin-yang-anticlockwise-spin; animation-duration: 4s; animation-timing-function: linear; animation-iteration-count: infinite; animation-play-state: paused; width: 256px; height: 256px; margin: 0px; padding: 0px;">
      <svg xmlns="http://www.w3.org/2000/svg" height="256" width="256" viewBox="-8 -8 16 16" style="animation-name: yin-yang-clockwise-spin; animation-duration: 4s; animation-timing-function: linear; animation-iteration-count: infinite; animation-play-state: paused; width: 256px; height: 256px; margin: 0px; padding: 0px;">
        <g>
          <path d="m0-7a3.5 3.5 0 1 1 0 7 3.5 3.5 0 1 0 0 7 7 7 0 1 1 0-14z" fill="#ccf"></path>
          <path d="m0-7a7 7 0 1 1 0 14 3.5 3.5 0 1 1 0-7 3.5 3.5 0 1 0 0-7z" fill="#004"></path>
          <circle cy="-3.5" r="1.1" fill="#004"></circle>
          <circle cy="3.5" r="1.1" fill="#ccf"></circle>
        </g>
      </svg>
    </div>
</div>

<style>
  .page-container {
    width: 100%;
    height: 100%; /* Ensure it takes full height to allow vertical centering */
    display: flex;
    flex-direction: column; /* Arrange items vertically */
    align-items: center; /* Center horizontally */
    justify-content: center; /* Center vertically */
  }
  
  .content-card {
    background: url('../assets/images/cards/Paper.png') center/cover;
    border: 3px solid #8b7355;
    border-radius: 15px;
    padding: 2rem;
    box-shadow: 0 4px 8px rgba(139, 115, 85, 0.2);
  }
  
  h2 {
    color: #8b7355;
    margin: 0 0 1rem 0;
    font-size: 2rem;
    font-weight: 300;
    text-align: center;
  }
  
  p {
    color: #6b5b47;
    font-size: 1.1rem;
    line-height: 1.6;
    margin: 0 0 1rem 0;
  }
  
  .feature-info {
    margin-top: 2rem;
    padding: 1.5rem;
    background: rgba(139, 115, 85, 0.1);
    border-radius: 10px;
    border: 1px solid rgba(139, 115, 85, 0.2);
  }
  
  .feature-info h3 {
    color: #8b7355;
    margin: 0 0 1rem 0;
    font-size: 1.3rem;
  }
  
  .feature-info ul {
    color: #6b5b47;
    padding-left: 1.5rem;
  }
  
  .feature-info li {
    margin-bottom: 0.5rem;
  }

  /* Yin Yang Spinner styling */
  .yin-yang {
    width: 256px;
    height: 256px;
    margin: 0px auto;
    padding: 0px;
    animation-duration: 4s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-play-state: paused;
  }

  .yin-yang svg {
    width: 256px;
    height: 256px;
    margin: 0px;
    padding: 0px;
    animation-duration: 4s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-play-state: paused;
  }

  .yin-yang.spinning {
    animation-name: yin-yang-anticlockwise-spin;
  }

  .yin-yang.spinning svg {
    animation-name: yin-yang-clockwise-spin;
  }

  @keyframes yin-yang-anticlockwise-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(-360deg); }
  }

  @keyframes yin-yang-clockwise-spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }
</style>
