<script>
 import { onMount } from 'svelte';

onMount(() => {

let isDragging = false;
  let startX, startY, initialTranslateX = 0, initialTranslateY = 0;

  function handleStart(event) {
    // Check if touch events are supported (for larger screens)
    const isTouch = event.touches && event.touches.length > 0;

    // Check if the target is the body
    if ((event.target.tagName.toLowerCase() === 'body' && !isTouch) || isTouch) {
      isDragging = true;
      startX = (isTouch ? event.touches[0].pageX : event.pageX) || 0;
      startY = (isTouch ? event.touches[0].pageY : event.pageY) || 0;
      document.body.style.cursor = 'grabbing';
    }
  }

  function handleMove(event) {
    if (!isDragging) return;
    const currentX = (event.touches ? event.touches[0].pageX : event.pageX) || 0;
    const currentY = (event.touches ? event.touches[0].pageY : event.pageY) || 0;

    const deltaX = currentX - startX;
    const deltaY = currentY - startY;

    startX = currentX;
    startY = currentY;

    initialTranslateX += deltaX;
    initialTranslateY += deltaY;

    document.body.style.transform = `translate(${initialTranslateX}px, ${initialTranslateY}px)`;
  
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
<div id="cardContainer">
    <div class="card" id="card1"> 
      <img src="yolijn.png" alt="illustratie van Yolijn"> 
      <h2>Yolijn van der Kolk</h2>
    </div>

    <div class="card" id="card2"> 
      <img src="yolijn.png" alt="illustratie van Yolijn"> 
      <h2>Yolijn van der Kolk</h2>
    </div>

    <div class="card" id="card3"> 
      <img src="yolijn.png" alt="illustratie van Yolijn"> 
      <h2>Yolijn van der Kolk</h2>
    </div>
    <!-- Add more cards as needed -->
</div>

<style>

    	#cardContainer {
		width: 100%;
		/* Set the width to 100% to cover the entire body */
		height: 100%;
		/* Set the height to 100% to cover the entire body */
		position: fixed;
		top: 0;
		left: 0;
		pointer-events: none;
		/* Allow pointer events to "pass through" the container */
	}

	.card {
		width: 45vw;
		/* Set the width of the cards */
		height: auto;
		/* Set the height of the cards */
		position: absolute;
		background-color: white;
		border: 1px solid #000000;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
	}

  .card h2{
  font-family: 'Fira Code', sans-serif;
  font-size: 1rem;
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
