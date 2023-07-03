<script>
</script>

<template>
    <div id="container-home" class="d-flex justify-content-between align-items-center">
        <div class="ms-2">
            <h1>Stefano Portfolio</h1>
            <router-link class="btn btn-warning" :to="{ name: 'projects' }">My latest projects</router-link>
        </div>
        <img src="../assets/IMG-20230105-WA0037.jpg" alt="">
    </div>
</template>

<style lang="scss" scoped>
#bottone-bianco{
    color: var(--color-neon);
    font-size: 2rem;
    border: var(--color-neon) 0.125em solid;
    padding: .25em 1em;
    border-radius: 0.25em;
    text-shadow: 
        0 0 0.125em hsl(0 0% 100% / 0.2),
        0 0 0.45em var(--color-neon);
    box-shadow: 
        inset 0 0 0.5em 0 var(--color-neon),
        0 0 0.5em 0 var(--color-neon);
    position: relative;
    z-index: 1;
}

#bottone-bianco::before{
    content: '';
    position: absolute;
    top: 70%;
    left: -90%;
    width: 280%;
    height: 100%;
    background: var(--color-neon);
    filter: blur(1em);
    transform: perspective(0.5em) rotateX(40deg) scale(1, 0.35) translateZ(-0.5em);
    opacity: 0.7;
    z-index: 0;
}

#bottone-bianco::after{
    content: '';
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: var(--color-neon);
    box-shadow: 0 0 2em 0.5em var(--color-neon);
    opacity: 0;
    transition: opacity 200ms linear;
}

#bottone-bianco:hover::before{
    opacity: 1;
}

#bottone-bianco:hover::after{
    opacity: 1;
    z-index: -1;
}

#bottone-bianco:hover{
    background: var(--color-neon);
    color: hsl(180, 100%, 50%);
    text-shadow: none;
    filter: blur(0,3em);
    font-weight: bold;
}

h1{
    color: white;
    text-shadow: 0 0 3px #eed621, 0 0 5px #000000;
}
#container-home{
    height: calc(100vh - 56px);
    
    img{
        height: 100%;
        
    }
}

</style>