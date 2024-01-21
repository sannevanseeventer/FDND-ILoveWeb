<script>

</script>

<section>
<a href="/"><h1>Verken mijn notities door te slepen</h1></a>

<div class="cursor-animation"></div>

</section>



<style>

    section{
        width: 100vw;
        height: 100vh;
    }

    h1 {
    font-family: 'Bebas Neue', sans-serif;
    color: black;
    text-align: center;
    font-size: 1.8rem;
    padding: 0.8rem 1.45rem;
    background-color: #fcfbf6;
    position: relative;
    z-index: 999;
    border: 1px solid black;
    top: 24.6vh;
    left: 3rem;
    max-width: 15rem;;
  }
  
  h1::before {
    content: '';
    position: absolute;
    z-index: -2;
    right: -5px;
    bottom: -5px;
    width: 100%;
    height: 100%;
    background: #fcfbf6;
    border: 1px solid black;
  }

  a{
    text-decoration: none;
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
    background-image: url('/hand-open.png');
  }
  50% {
    background-image: url('/hand-dicht.png');
  }
}

</style>