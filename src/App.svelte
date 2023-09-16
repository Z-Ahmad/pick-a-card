<!-- App.svelte -->
<style>
  body {
    margin: 0;
    padding: 0;
    transition: background-color 0.5s; /* Add a smooth transition effect */
  }

  .app {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
  }
</style>

<script>
  import { onMount } from 'svelte';

  import Card from './components/Card.svelte';

  const cardColors = ['#3498db', '#f1c40f', '#e74c3c']; // Blue, Yellow, Red
  const cardImages = ['/blueCard.png', '/goldCard.png', '/redCard.png']

  let currentIndex = 0;
  let isShuffling = true;

  function rotateCard() {
    if (isShuffling) {
      currentIndex = (currentIndex + 1) % cardColors.length;
      document.body.style.backgroundColor = cardColors[currentIndex]; // Change the background color
    }
  }

  function handleKeyDown(event) {
    if (event.key === 'w') {
      if (!isShuffling) {
        // If 'W' is pressed to resume, reset currentIndex to random card
        currentIndex = Math.floor(Math.random() * 3);;
        document.body.style.backgroundColor = cardColors[currentIndex]; // Reset background color
      }
      isShuffling = !isShuffling; // Toggle the shuffling state
    }
  }

  // Listen for keyboard events
  window.addEventListener('keydown', handleKeyDown);

  // Automatically rotate the card every 0.5 seconds
  let intervalId;
  onMount(() => {
    intervalId = setInterval(rotateCard, 500); // Rotate every 0.5 seconds
  });
</script>

<div class="app">
  <!-- <Card color={cardColors[currentIndex]} /> -->
  <img src={cardImages[currentIndex]} alt="current card">
</div>
<h1>Press w to start/stop</h1>
<img src="/pixelTF.png" alt="">
