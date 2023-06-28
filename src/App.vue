<script>
import axios from 'axios';
import ProjectCard from './components/ProjectCard.vue'
export default{
  components: {
    ProjectCard
  },
  data(){
    return{
      projects:[],
      baseUrl: 'http://127.0.0.1:8000'
    }
},
mounted(){
	this.getProjects();
},
methods:{
	getProjects(){
		axios.get(`${this.baseUrl}/api/projects`)
		.then(res=>{
		this.projects=res.data.projects
		})
	}
}
}
</script>

<template>
  <div class="container d-flex flex-wrap">
    <ProjectCard v-for="(elem,index) in projects" :key="index" :propsProject="elem"/>
  </div>
</template>

<style lang="scss">
@use './style/main.scss';
.d-flex{
  gap: 40px;
}
</style>
