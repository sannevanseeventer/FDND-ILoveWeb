<script>

</script>

<div class="start-container">

<div class="shadow-container"></div>
<h1>Verken mijn notities door te slepen</h1>

</div>

<div class="cursor-animation"></div>




<style>

.start-container{
    width: 100vw;
    height: auto;
    position: absolute;
    margin-top: 2.3rem;
}

    h1{
        font-size: 2rem;
        color: black;
        font-family: 'Bebas Neue', sans-serif;
        background-color: #fcfbf6;
        border: 1px solid black;
        padding: .55rem 2.2rem;
        position: absolute;
        z-index: 1001;
        max-width: 15rem;
        left: 4.9vh;
        top: 21.1vh;
        text-align: center;
    }

    .shadow-container{
        padding: .55rem 2.2rem;
        position: absolute;
        z-index: 1001;
        left: 3.7vh;
        top: 23.3vh;
        width: 15rem;
        height: 4.8rem;
        background-color: #fcfbf6;
        border: 1px solid black;
    }

 
.cursor-animation {
  width: 3rem;
  height: 10rem;
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
  z-index: 1001;
  animation: cursorAnimation 2s infinite steps(1);
  transition: none;
  left: 23vh;
  top: 50vh;
}

@keyframes cursorAnimation {
  0%, 100% {
    background-image: url('./hand-open.png');
  }
  50% {
    background-image: url('./hand-dicht.png');
  }
}

</style>