<script>
export default{
        name: "ProjectCard",
        props: ['propsProject'],
    data(){
        return{
          
          baseUrl: 'http://127.0.0.1:8000'
        }
    },
}
</script>
<h3></h3>
<template>
<div class="card" style="width: 18rem;">
  <img :src="`${baseUrl}/storage/${propsProject.img}`" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Title <br>{{ propsProject.name }}</h5>
    <p class="card-text">Description: <br>{{ propsProject.description }}</p>
    <p class="card-text">Client: {{ propsProject.client }}</p>
    <p class="card-text">Project Type: {{propsProject.type.name}}</p>
    <ul id="mario" class="card-text"> 
        Technology used:
        <li v-for="(elem,index) in propsProject.technologies" :key="index" id="pino">{{elem.name}}</li>
    </ul>
  </div>
</div>
</template>

<style lang="scss">
.card{
    width: 100px;
}
#mario{
    padding-left: 0;
    #pino{
        text-decoration: underline;
    }
}
*{
    list-style-type: none;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>
