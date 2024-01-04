<script>
 import { onMount } from 'svelte';

onMount(() => {
  let isDragging = false;
    let startX, startY, initialTranslateX = 0, initialTranslateY = 0;

    // Get the container for draggable content
    const draggableContainer = document.getElementById('draggableContainer');

    function handleStart(event) {
      // Prevent default behavior to avoid scrolling
      event.preventDefault();

      isDragging = true;
      startX = event.touches ? event.touches[0].pageX : event.pageX;
      startY = event.touches ? event.touches[0].pageY : event.pageY;
      document.body.style.cursor = 'grabbing';
    }

    function handleMove(event) {
      if (!isDragging) return;
      // Prevent default behavior to avoid scrolling
      event.preventDefault();

      const currentX = event.touches ? event.touches[0].pageX : event.pageX;
      const currentY = event.touches ? event.touches[0].pageY : event.pageY;

      const deltaX = currentX - startX;
      const deltaY = currentY - startY;

      startX = currentX;
      startY = currentY;

      initialTranslateX += deltaX;
      initialTranslateY += deltaY;

      draggableContainer.style.transform = `translate(${initialTranslateX}px, ${initialTranslateY}px)`;
    }

    function handleEnd() {
      isDragging = false;
      document.body.style.cursor = 'grab';
    }

    document.body.addEventListener('mousedown', handleStart);
    document.addEventListener('mousemove', handleMove);
    document.addEventListener('mouseup', handleEnd);

    // Touch events for mobile and larger screens
    document.body.addEventListener('touchstart', handleStart);
    document.addEventListener('touchmove', handleMove);
    document.addEventListener('touchend', handleEnd);

});
  </script>

<!-- Non-draggable content container -->
<div id="nonDraggableContent">
<h1>Blog</h1>
<button>Menu</button>
</div>
<!-- Draggable content container -->
<div id="draggableContainer">
  <div id="cardContainer">
    <a href="/BlogPost">
      <div class="card" id="card1">
        <img src="yolijn.png" alt="illustratie van Yolijn">
        <h2>Yolijn Kolk</h2>
      </div>
    </a>

    <div class="card" id="card2">
      <img src="ischa.png" alt="illustratie van Ischa">
      <h2>Ischa Gast</h2>
    </div>

    <div class="card" id="card3">
      <img src="yolijn.png" alt="illustratie van Yolijn">
      <h2>Yolijn van der Kolk</h2>
    </div>
  </div>
</div>

<style>
  #nonDraggableContent {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 2; /* Above the draggable content */
  }

  h1 {
    position: absolute;
    top: 3rem;
    left: 6rem;
    font-size: 5rem;
    font-weight: bold;
    font-family: 'Bebas Neue', sans-serif;
    z-index: 1001;
  }

  button {
    position: absolute;
    top: 3rem;
    left: 16rem;
    font-size: 1.5rem;
    z-index: 1001;
  }

  #draggableContainer {
    width: 100%;
    height: 100%;
    overflow: hidden; /* Prevent content from disappearing outside the viewport */
    touch-action: none; /* Disable default touch actions, including scrolling */
  }

  #cardContainer {
    width: 100%;
    height: 100%;
    /* pointer-events: none; Remove this line */
  }

  .card {
    width: 45vw;
    /* Set the width of the cards */
    height: auto;
    /* Set the height of the cards */
    position: fixed; /* Fix the cards within the viewport */
    background-color: #fcfbf6;
    border: 1px solid #000000;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
  }

  a{
    all: unset;
  }

  /* h1{
    position: absolute;
    top: 3rem;
    left: 6rem;
    font-size: 5rem;
    font-weight: bold;
    font-family: 'Bebas Neue', sans-serif;
    z-index: 1001;
} */
  

  .card h2{
  font-family: 'Fira Code', sans-serif;
  font-size: 1rem;
  margin-bottom: 1rem;
  }

  .card img{
    width: 7rem;
    height: auto;
  }

	#card1 {
		top: 30vh;
		left: 10vw;
	}

	#card2 {
		top: 60vh;
		left: 80vw;
	}

	#card3 {
		top: 120vh;
		left: 100vw;
	}
</style>
