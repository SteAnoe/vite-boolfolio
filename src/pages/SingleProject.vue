<script>
import axios from 'axios';

export default{
  name: 'SingleProject',
  data(){
    return{
      project: null,
      baseUrl: 'http://127.0.0.1:8000'
    }
},
created(){
	this.getSingleProjects();
},
methods:{
	getSingleProjects(){
		axios.get(`${this.baseUrl}/api/projects/${this.$route.params.slug}`)
		.then((response)=>{
            if(response.data.success) {
                this.project = response.data.project;
            }
            else {
                this.$router.push({name: 'NotFound'})
            }
		
		})
	}
}
}
</script>

<template>
    
    <div class="container d-flex justify-content-center align-items-center">
        <div class="card" style="width: 25rem; padding: 10px;">
            <img :src="`${baseUrl}/storage/${project.img}`" class="card-img" alt="...">
            <div class="card-body">
              <h5 class="card-title">{{ project.name }}</h5>
            
              <div class="d-flex justify-content-between">
                  <div>
                      <p v-if="project.type" class="card-text">
                          <span class="text-bold">Project Type:</span>  
                          <br>
                          {{project.type.name}}
                      </p>    
                  </div>
                  <div class="right">
                      <ul id="mario" class="card-text" v-if="project.technologies"> 
                          <span class="text-bold">Technology used:</span> 
                          <li v-for="(elem,index) in project.technologies" :key="index" id="pino">{{elem.name}}</li>
                      </ul>
                  </div>
              </div>
              <p class="card-text" id="desc">
                  <span class="text-bold">Description:</span> 
                  <br>
                  {{ project.description }}
              </p>      
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
 h1{
    color:white
 }
</style>
