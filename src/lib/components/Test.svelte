<script>
    import { onMount } from 'svelte';

onMount(() => {
    const container = document.querySelector('.container');
    let isDragging = false;
    let startX, startY, initialLeft, initialTop;

    container.addEventListener('mousedown', (e) => {
      isDragging = true;
      startX = e.clientX;
      startY = e.clientY;
      initialLeft = container.offsetLeft;
      initialTop = container.offsetTop;

      document.addEventListener('mousemove', handleMouseMove);
      document.addEventListener('mouseup', handleMouseUp);
    });

    function handleMouseMove(e) {
      if (isDragging) {
        e.preventDefault();
        const x = e.clientX;
        const y = e.clientY;
        const moveX = x - startX;
        const moveY = y - startY;

        container.style.left = initialLeft + moveX + 'px';
        container.style.top = initialTop + moveY + 'px';
      }
    }

    function handleMouseUp() {
      isDragging = false;
      document.removeEventListener('mousemove', handleMouseMove);
      document.removeEventListener('mouseup', handleMouseUp);
    }
  });
  </script>

<div class="container">
<!-- Speakers We love Web -->
    <div class="card" id="card1">
        <div class="card-container">
        <img src="yolijn.png" alt="illustratie van Yolijn">
        <h2>Yolijn van der Kolk</h2>
    </div>
</div>

    <div class="card" id="card2">
        <div class="card-container">
        <img src="ischa.png" alt="illustratie van Ischa Gast">
        <h2>Ischa Gast</h2>
    </div>
</div>

    <div class="card" id="card3">
        <div class="card-container">
        <img src="yolijn.png" alt="illustratie van Yolijn">
        <h2>Yolijn van der Kolk</h2>
    </div>
</div>
</div>

  <style>
.container {
    position: absolute;
    width: 300%;
    height: 300%;
    top: 0;
    left: 0;
    background-image: linear-gradient(rgba(0, 0, 0, 0.1) 1px, transparent 1px), linear-gradient(90deg, rgba(0, 0, 0, 0.1) 1px, transparent 1px);
	background-size: 3rem 3rem;
}

.container:active {
    cursor: grabbing; /* Verandert de cursor naar grabbing tijdens het slepen */
}
.card {
    width: 11.9rem;
    height: 14.9rem;
    background-color: #fcfbf6;
    position: absolute;
    cursor: pointer;
}

.card-container{
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    margin-top: 1rem;
}

#card1 {
	top: 6.1rem;
	left: 6.1rem;
}

#card2 {
	top: 24.1rem;
	left: 33.1rem;
}

#card3 {
	top: 39.1rem;
	left: 15.1rem;
	}

h2{
    font-family: 'Fira Code', sans-serif;
    font-size: .9rem;
    margin-bottom: 1rem;
    }

img{
    width: 7rem;
    height: auto;
}

  </style>