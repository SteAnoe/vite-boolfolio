<script>


export default{
    name: "AppHeader",
  data(){
    return{
      
    }
},
mounted(){

},
methods:{

}
}
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
            <router-link class="navbar-brand" :to="{ name: 'contacts' }">
                <img src="../assets/avatar_8.jpg" alt="" class="rounded-circle">
                Stefano Anoè
            </router-link>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link class="nav-link" aria-current="page" :to="{ name: 'home' }">Home</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" :to="{ name: 'about' }">About</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" :to="{ name: 'projects' }">Projects</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
nav{
    height: 56px;
    box-shadow: 0 1px 30px #FFCA2C;
    img{
        height: 48px;
    }
    #navbarNav{
        justify-content: flex-end;
    }
    .router-link-active{
        color: #FFCA2C;
        font-weight: bold;
    }
}

</style>
