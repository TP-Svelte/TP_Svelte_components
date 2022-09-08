<script>
    import { flip } from 'svelte/animate';
    export let darkMode;
    export let images;
    export let imageWidth = 300;
    export let imageSpacing = 20; 
    export let speed = 50; 
    
    const rotateRight = e => {
    
        const transitioningImage = images[images.length - 1];
        document.getElementById(transitioningImage.id).style.opacity = "0";
        images = [images[images.length - 1],...images.slice(0, images.length - 1)];
        setTimeout(() => (document.getElementById(transitioningImage.id).style.opacity = "1"), speed); 
    
    }
    
    const rotateLeft = e => {
        const transitioningImage = images[0];
        images = [...images.slice(1, images.length), images[0]]; 
        document.getElementById(transitioningImage.id).style.opacity = "0";
        setTimeout(() => (document.getElementById(transitioningImage.id).style.opacity = "1"), speed);
    
    
    }
    
    </script>
    
    
    <div class="carousel-container">
        <div class="carousel-images">
            {#each images as image (image.id)}
                <img 
                src={image.image_url} 
                alt={image.id}
                id={image.id}
                style={`width:${imageWidth}px; margin: 0 ${imageSpacing}px;`}
                animate:flip={{duration: speed}}/> 
            {/each}
        </div>
        <div class="carousel-button">
            <button class={darkMode ?  'button-dark' : 'button-light'} id="left" on:click={rotateRight}> Left </button>
            <button  class={darkMode ?  'button-dark' : 'button-light'} id="right" on:click={rotateLeft}> Right </button>
         </div>
    
    
    </div>
    
    
    <style>
        img {
            width: 300px !important;
            height: 300px;
            object-fit: cover;
        }
        .carousel-container{
            margin-top: 2em;
            /* width: 100vw; */
            overflow-x: hidden; 
            max-width: 100vw;
        }
        .carousel-images{
            display : flex; 
            flex-wrap : nowrap; 
            justify-content: center; 
            align-items: center; 
        }
        .carousel-button {
            margin-top: 2em;
            display: flex;
            gap: 30px;
            justify-content: center;
            
        }
        .button-light {
        background-color: rgba(0,220,130,1);
        color: black;
        transition: 0.4s all ease-in-out;
    }
    .button-dark {
        background-color: #00181E;
        color: #E6FCF3;
        transition: 0.3s all ease-in-out;

    }
    </style>
    