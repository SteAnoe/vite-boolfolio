<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue'
export default{
  components: {
    ProjectCard
  },
  data(){
    return{
      projects:[],
      baseUrl: 'http://127.0.0.1:8000',
      currentPage: 1,
      lastPage: null,
      types: null,
      selectedType: "all" ,
      technologies: null,
      selectedTechnologies: []
    }
},
mounted(){
	this.getProjects(1);
  this.getTypes();
  this.getTechnologies();
},
watch: {
	selectedTechnologies: {
	  handler: 'getProjects',
	  deep: true
	}
},
methods:{
	getProjects(projectApiPage){
    const params = {
      page: projectApiPage
    }

    if(this.selectedType !== 'all'){
      params.type_id = this.selectedType
    }

    if(this.selectedTechnologies.length > 0){
	    params.technologies_ids = this.selectedTechnologies.join(',');
    }

		axios.get(`${this.baseUrl}/api/projects`, { params }).then(res=>{
		this.projects=res.data.projects.data
    this.currentPage = res.data.projects.current_page
    this.lastPage = res.data.projects.last_page
		})
	},
  getTypes(){
    axios.get(`${this.baseUrl}/api/types`).then(res => {
      this.types = res.data.types
    })
  },
  getTechnologies(){
    axios.get(`${this.baseUrl}/api/technologies`).then(res => {
      this.technologies = res.data.technologies
    })
  }
}
}
</script>

<template>
  <div class="mb-3">
    <label for="" class="form-label">Types Filter</label>
    <select @change="getProjects()" v-model="selectedType" class="form-select form-select-lg" name="" id="">
      <option value="all"> -- All -- </option>
      <option v-for="(elem, index) in types" :key="index" :value="elem.id">{{elem.name}}</option>  
    </select>
  </div>

  <div class="mb-3">
    <h2>Technologies Filter</h2>
    <label for="" v-for="(elem,index) in technologies" :key="index">
      <input type="checkbox" :value="elem.id" v-model="selectedTechnologies">
      {{ elem.name }}
    </label>
  </div>

  <div id="container-proj" class="container d-flex flex-wrap">
    <ProjectCard v-for="(elem,index) in projects" :key="index" :propsProject="elem"/>
  </div>

  <ul class="pagination">
      <li class="page-item">
        <a class="page-link" @click.prevent="getProjects(currentPage-1)" href="#" aria-label="Previous">
          <span aria-hidden="true" >&laquo;</span>
        </a>
      </li>
      <li class="page-item" v-for="(elem,index) in lastPage" :key="index" :class="(currentPage === elem) ? 'active' : ''">
        <a class="page-link" href="#" @click.prevent="getProjects(elem)">{{ elem }}</a>
      </li>
      <li class="page-item">
        <a class="page-link" @click.prevent="getProjects(currentPage+1)" href="#" aria-label="Next">
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>
    </ul>
</template>

<style lang="scss" scoped>
#container-proj{
  // height: calc(100vh - 56px);
  gap: 40px;
  margin-top: 100px;
  margin-bottom: 100px;
}


</style>
