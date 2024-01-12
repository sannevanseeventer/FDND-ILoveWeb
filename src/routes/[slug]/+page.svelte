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
        <h1>{data.blogPost.title}</h1>
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
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        background-image: linear-gradient(rgba(0, 0, 0, 0.300) 1px,transparent 1px),
        linear-gradient(90deg, rgba(0, 0, 0, 0.300) 1px, transparent 1px);
        background-size: 1.5rem 1.5rem;
        background-color: #fcfbf6;
        z-index: 1;
    }


  </style>