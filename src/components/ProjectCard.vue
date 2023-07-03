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
  <!-- <img :src="`${baseUrl}/storage/${propsProject.img}`" class="card-img" alt="..."> -->
  <div class="card-body">
    <router-link class="router-link" :to="{name: 'SingleProject', params: {slug: propsProject.slug}}"><h5 class="card-title">{{ propsProject.name }}</h5></router-link>
    
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
  </div>
</div>
</template>

<style lang="scss">
.router-link{
    text-decoration: none;
    color: black;
}
:root{
    --gradient: linear-gradient(
      45deg,
      #845ec2,
      #d65db1,
      #ff6f91,
      #ff9671,
      #ffc75f,
      #f9f871  
    );
    --gradient2: linear-gradient(
      45deg,
      #d0ca24 0%,
      #2b2a2b 35%,
      #2b2a2b 65%,
      #ffffff 80%
    );
    --gradient-2: linear-gradient(
        53deg, 
        rgba(180,34,195,1) 0%, 
        rgba(13,18,162,1) 45%, 
        rgba(45,253,100,1) 90%
    );
    --color-neon2: hsl(317 100% 54%);
    --color-neon: hsl(60 100% 54%);
}

.card{
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
