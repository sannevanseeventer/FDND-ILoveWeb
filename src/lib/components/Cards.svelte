<script>
    export let data;
import { onMount } from "svelte";
    import Start from "./Start.svelte";
    import Sketches from "./Sketches.svelte";
    import Title from "./Title.svelte";

onMount(() => {
    const container = document.querySelector(".container");
    const section = document.querySelector("section");

    let isDragging = false;
    let startX, startY, initialLeft, initialTop;

    container.addEventListener("mousedown", (e) => {
        isDragging = true;
        startX = e.clientX;
        startY = e.clientY;
        initialLeft = container.offsetLeft;
        initialTop = container.offsetTop;

        document.addEventListener("mousemove", handleMouseMove);
        document.addEventListener("mouseup", handleMouseUp);
    });

    function handleMouseMove(e) {
        if (isDragging) {
            e.preventDefault();
            const x = e.clientX;
            const y = e.clientY;
            const moveX = x - startX;
            const moveY = y - startY;

            const containerWidth = container.offsetWidth;
            const containerHeight = container.offsetHeight;
            const sectionWidth = section.offsetWidth;
            const sectionHeight = section.offsetHeight;

            let newLeft = initialLeft + moveX;
            let newTop = initialTop + moveY;

            // Restrict movement within section boundaries
            if (newLeft > 0) {
                newLeft = 0;
            } else if (newLeft < sectionWidth - containerWidth) {
                newLeft = sectionWidth - containerWidth;
            }

            if (newTop > 0) {
                newTop = 0;
            } else if (newTop < sectionHeight - containerHeight) {
                newTop = sectionHeight - containerHeight;
            }

            container.style.left = newLeft + "px";
            container.style.top = newTop + "px";
        }
    }

    function handleMouseUp() {
        isDragging = false;
        document.removeEventListener("mousemove", handleMouseMove);
        document.removeEventListener("mouseup", handleMouseUp);
    }

    window.onload = function() {
    // Verplaats het venster naar een standaardpositie
    window.moveTo(0, 0);

};
});
</script>

<section>



    <div class="container">       
        <Start />
        <Title />
        <Sketches />

        <!-- Speakers We love Web -->
            {#each data.blogPosts as post}
                <a href="/{post.slug}">
                    <div class="card" style="top: {post.top}rem; left: {post.left}rem">
                        <div class="card-container">
                            <img src="{post.image.url}" alt="" />
                            <h2>{post.title}</h2>
                        </div>
                        <img class="subject" src="{post.subjectImage.url}" alt="subject" style="transform: translateY({post.subjectTop}rem); margin-left: {post.subjectLeft}rem;">
                    </div>
                </a>
            {/each}
    </div>
</section>



<style>
    section {
        height: 100vh;
        width: 100vw;
        overflow: hidden;
    }


    .container {
        position: absolute;
        width: 400%;
        height: 400%;
        top: 0;
        left: 0;
        background-image: linear-gradient(rgba(0, 0, 0, 0.300) 1px,transparent 1px),
        linear-gradient(90deg, rgba(0, 0, 0, 0.300) 1px, transparent 1px);
        background-size: 1.5rem 1.5rem;
        background-color: #fcfbf6;
        z-index: 1;
    }

    .container:active {
        cursor: grabbing;
    }
    
    .card {
        width: 11.9rem;
        height: 14.9rem;
        background-color: #fcfbf6;
        position: absolute;
        cursor: pointer;
    }

    .subject {
        position: relative;
        width: 10.5rem;
        height: auto;
    }

    .card-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-direction: column;
        margin-top: 1.6rem;
    }

    h2 {
        font-family: "Fira Code", sans-serif;
        font-size: 0.9rem;
        margin-top: 1rem;
        margin-bottom: 1rem;
    }

    img {
        width: 7rem;
        height: auto;
    }

    a{
    all: unset;
  }
  
</style>