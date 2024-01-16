<script>
    export let data;
  </script>
  
  <svelte:head>
    <title>{data.blogPost.title}</title>
  </svelte:head>
  
  <main>
    <section>
<div  class="container">
  
    {#if data.blogPost}
        <h3>{data.blogPost.title}</h3>
        <p>{@html data.blogPost.content.html}</p>
    {:else}
      <p>Post not found.</p>
    {/if}

</div>
</section>
  </main>


  <style>
 section {
        height: 100vh;
        width: 100vw;
        overflow: hidden;
    }

    .container {
        position: absolute;
        width: 100vw;
        height: auto;
        top: 0;
        left: 0;
        background-image: linear-gradient(rgba(0, 0, 0, 0.300) 1px,transparent 1px),
        linear-gradient(90deg, rgba(0, 0, 0, 0.300) 1px, transparent 1px);
        background-size: 1.3rem 1.3rem;
        background-color: #fcfbf6;
        z-index: 1;
    }

    h3{
        font-size: 2rem;
        background-color: #A6EFFF;
        width: 15rem;
        height: 13.3rem;
        margin-left: 1.3rem;
        border: 1px solid black;
        font-family: 'Fira Code';
    }

    p{
        font-family: 'Fira Code', sans-serif;
        background-color: #fcfbf6;
        max-width: 18rem;
        padding: .4rem 1.35rem;
        margin: 3.5rem auto;
        font-size: 1rem;
        border: 1px solid black;
    }


  </style>