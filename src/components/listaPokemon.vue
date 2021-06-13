<template>
  
   <div v-if="show_container" class="container">
   
   <div id="big_input" class="card">
   
    <div class="input-group">
                 <i class="fas fa-search iconsearch"></i>
                  <input type="text" id="input_search" class="form-control rounded" 
                  placeholder="Search"
                   />
                </div></div>
    
    <div id=results_of_search>
        {{data_de_pokemon}}
    </div>
    <table border="1px">
        <tr>
            <td>Nombre</td>
            <td>url</td>
        </tr>
        <tr v-for="item in list_allpokemon" v-bind:key="item.url">
            <td>{{item.name}}</td>
            <td @click="data_this_pokemon(item.url)">{{item.url}}</td>
        </tr>
    </table>
    </div>
    
  

</template>


<script>
import {bus} from '../main';

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)

export default {
  name: 'ListaPokemon',
  data(){
      return{
          show_container:false,
          data_de_pokemon:'',
          list_allpokemon:undefined
      }
  },
  methods:{
      data_this_pokemon(url_this_pokemon){
           Vue.axios.get(url_this_pokemon)
    .then((resp)=>{
        console.log(resp.data.name+" "+resp.data.height)
    }

    )
      }
  },

   created(){
    bus.$on('sendData',(data)=>{
      this.show_container=data;
      console.log('show container is '+this.show_container)
    })
  },
  mounted(){
    Vue.axios.get('https://pokeapi.co/api/v2/pokemon')
    .then((resp)=>{
        this.list_allpokemon=resp.data.results;
        console.warn(resp.data.results)
        
    }

    )
}

}
</script>

<style>
.container{
    padding:0px;
    display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
}

#results_of_search{
    margin-top:40px;
 height:106px;
  width:106px;
  border-style: solid;
  border-width:1px;
  border-color:red;
 /*border-bottom:1px solid rgba(0,0,0,0.1);*/
  overflow:hidden;
}

.card-body{
    max-width:100%;
max-height:100%;
}

.input-group{
    height:50px;
}

.iconsearch{
     font-size:18px;
     color:#BFBFBF;
     height:18px;

     margin-left:15px;
     margin-top:auto;
     margin-bottom:auto;
}

#input_search{
    padding-right:10px;
    padding-left:10px;

    font-family:'Montserrat';
  font-style: normal;
  font-weight: 500;

  font-size:16px;
  line-height:140%;
  
  color:#353535;
  border:none;
  text-decoration: none;
  background-color:#FFFFFF;
  
}

#input_search:focus{
   outline:none;
  box-shadow: none;
}
::-webkit-input-placeholder {
  color: #BFBFBF !important;
}

@media screen and (max-width: 575px) {
  
#big_input{
  margin-top:35px;
  height:50px;
  width:315px;
 
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  box-shadow:0px 2px 10px rgba(0,0,0,0.04);
   border:none;
   
}
        
}

@media screen and (min-width: 576px) {
#big_input{
  margin-top:35px;
  height:50px;
  width:570px;
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  box-shadow:0px 2px 10px rgba(0,0,0,0.04);
   border:none;
  
}
        
}
</style>