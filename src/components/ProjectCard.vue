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
<div class="card" style="width: 25rem; padding: 10px;">
  <img :src="`${baseUrl}/storage/${propsProject.img}`" class="card-img" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ propsProject.name }}</h5>
    <div class="d-flex justify-content-between">
        <div>
            <p v-if="propsProject.type" class="card-text">
                <span class="text-bold">Project Type:</span>  
                <br>
                {{propsProject.type.name}}
            </p>    
        </div>
        <div class="right">
            <ul id="mario" class="card-text" v-if="propsProject.technologies"> 
                <span class="text-bold">Technology used:</span> 
                <li v-for="(elem,index) in propsProject.technologies" :key="index" id="pino">{{elem.name}}</li>
            </ul>
        </div>
    </div>
    <p class="card-text" id="desc">
        <span class="text-bold">Description:</span> 
        <br>
        {{ propsProject.description }}
    </p>      
  </div>
</div>
</template>

<style lang="scss">
.card{
    background-color: rgb(208, 250, 253) !important;
    img{
        max-height: 284px;
    }
    .card-body{
        border-top: 1px solid black;
        margin-top: 15px;
        .card-title{
            text-transform: capitalize;
            text-align: center;
            font-size: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid black;
        }
        .right{
            text-align: end;
        }
        #desc{
            text-align: center;
        }
    }
}
.text-bold{
    font-weight: bold;
    font-size: 15px;
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
