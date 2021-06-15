<template>
  
   <div v-if="show_container" class="container">
   <nav v-if="show_navbar" class="navbar fixed-bottom">
  
  <div class="row align-items-center">
  <div class="col">
  <button @click="inactive_pokemon=true" v-bind:style="{backgroundColor:inactive_pokemon?'#F22539':'#BFBFBF'}" id="button_all" type="button" class="btn float-end"><i id="icon_list" class="fas fa-list"></i><span class="label_text">All</span></button>
  </div>

  <div class="col">
  <button @click="inactive_pokemon=false" v-bind:style="{backgroundColor:!inactive_pokemon?'#F22539':'#BFBFBF'}" id="button_favorites" type="button" class="btn float-start"><i id="icon_star" class="fas fa-star"></i><span class="label_text">Favorites</span></button>
  </div>
  </div>
</nav>
   <div id="big_input" class="card">
   
    <div class="input-group">
                 <i class="fas fa-search iconsearch"></i>
                  <input type="text" id="input_search" class="form-control rounded" 
                  @keyup="focus_input_text()" v-model="text_model"
                  placeholder="Search"
                   />
                </div></div>
    <div v-if="show_no_results" id="no_results">
      <NoResults/>
    </div>
     <div id="list_of_results">
     <div v-for="(item,index) in list_allpokemon" v-bind:key="item.url">
          <!--<div @click="data_this_pokemon(item.url)" class="card pokemoncard">-->
                <template v-if="favoritePokemon(index)==='Favorito'">
                  <div @click="data_this_pokemon(item.url)" class="card pokemoncard">
                  <div class="row align-items-center pokedetails">
                    <div class="col">
                 <p class="text_pokename float-start">{{item.name | capitalize}}</p>
                    </div>
                    <div class="col">
               <!--  <template v-if="favoritePokemon(index)==='Favorito'">-->
                  <img class="icon_star float-end" src="../assets/img/active_star.png">
               <!--   </template>
                <template v-else>
                    <img class="icon_star float-end" src="../assets/img/inactive_star.png">
                 </template>-->
                    </div>
                  </div></div>
                </template>
                <template v-else>
                  <div v-show="inactive_pokemon" @click="data_this_pokemon(item.url)" class="card pokemoncard">
                   <div class="row align-items-center pokedetails">
                    <div class="col">
                 <p class="text_pokename float-start">{{item.name | capitalize}}</p>
                    </div>
                    <div class="col">
               <!--  <template v-if="favoritePokemon(index)==='Favorito'">-->
                  <img class="icon_star float-end" src="../assets/img/inactive_star.png">
               <!--   </template>
                <template v-else>
                    <img class="icon_star float-end" src="../assets/img/inactive_star.png">
                 </template>-->
                    </div>
                  </div></div>
                </template>
         <!-- </div>-->
    </div>
    </div>
    <div id="results_of_search">
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
import NoResults from '../components/noResults.vue'
import {bus} from '../main';

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)

export default {
  name: 'ListaPokemon',
   components: {
    NoResults,
  },
  data(){
      return{
          show_container:false,
          show_navbar:true,
          data_de_pokemon:'',
          list_allpokemon:undefined,
          text_model:'',
          show_no_results:false,
          inactive_pokemon:true,
         // show_modal:false,
         datapokemon_object:{}
      }
  },
   filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
},
  computed:{
  

  },
  methods:{
     favoritePokemon(index){
      //if(index==Math.floor(Math.random() * 20)) 
      return index===Math.floor(Math.random() * 20) ? 'Favorito':'No Favorito'
   },
      data_this_pokemon(url_this_pokemon){
     //   this.show_modal=true
           Vue.axios.get(url_this_pokemon)
    .then((resp)=>{
       console.log(resp.data)
        this.datapokemon_object={
          namePokemon:resp.data.name,
          heightPokemon:resp.data.height,
          weightPokemon:resp.data.weight,
          typesPokemon:resp.data.types,
          imgPokemon:resp.data.sprites.front_default,
        }
       // console.log('imagen: '+this.datapokemon_object.i)
         bus.$emit('busDataPokemon',this.datapokemon_object);
    }
 
    )
   
   // bus.$emit('busDataPokemon',this.datapokemon_object);
      }
      ,
      focus_input_text(){
        this.data_de_pokemon=''
        this.show_navbar=true
        this.show_no_results=false
        let text_model_lower=this.text_model.toLowerCase();
         for (let item_pokemon of this.list_allpokemon){
           let name_pokemon_lower=item_pokemon.name.toLowerCase();
           if(name_pokemon_lower.indexOf(text_model_lower)!==-1){
            this.data_de_pokemon+=item_pokemon.name+' - '
           }
       }
        if(this.data_de_pokemon===''){
           this.data_de_pokemon+='no hay'
           this.show_no_results=true
           this.show_navbar=false
       }
      }
  },

   created(){
    bus.$on('sendData',(data)=>{
      this.show_container=data;
      console.log('show container is '+this.show_container)
    })
    ,
    this.data_de_pokemon='hola'
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

.row{
  width:100%;
  margin:0;
}

.col{
  padding:0;
}

#list_of_results{
    margin-top:40px;
 
/*  width:106px;*/
  border-style: solid;
  border-width:1px;
  border-color:red;
  overflow:hidden;
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


#no_results{
    margin-top:50px;
 height:152px;
 /* width:106px;*/
 
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
#button_all, #button_favorites{
  width:150px;
}

#button_all{
  margin-right:7.5px;
}
#button_favorites{
  margin-left:7.5px;
}
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

#no_results{
  width:262px;
}

#list_of_results{
  width:315px;
}


.pokemoncard{
 margin-top:0px;
   margin-right:0px;
    margin-left:0px;
    margin-bottom:10px;
  width:315px;
  height:60px;
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  border:none;
  cursor:pointer;
}    
}

@media screen and (min-width: 576px) {
#button_all, #button_favorites{
  width:275px;
}

#button_all{
  margin-right:10px;
}
#button_favorites{
  margin-left:10px;
}
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


#no_results{
  width:570px;
}

#list_of_results{
  width:570px;
}

.pokemoncard{
  margin-top:0px;
  margin-right:0px;
  margin-left:0px;
  margin-bottom:10px;
  width:570px;
  height:60px;
  overflow:hidden;
  border-radius:5px;
  background-color:#FFFFFF;
  border:none;
  cursor:pointer;
}
        
}

.navbar{
  height:80px;
  background-color:#FFFFFF;
  box-shadow:0px -5px 4px rgba(0,0,0,0.5);
  z-index:2;
}

/*button{
  margin-left:0;
   margin-right:0;
  background-color:#BFBFBF;
}*/

#button_all, #button_favorites{
 /* background-color:#BFBFBF;*/
  height:44px;
  border-radius:60px;
  margin-top:auto;
  margin-bottom:auto;
  color:#FFFFFF;
}

#icon_list, #icon_star{
  font-size:22px;
  margin-right:11px;
   margin-top:auto;
   margin-bottom:auto;
}

.label_text{
  height:22px;
  font-family: 'Lato';
  font-style:normal;
  font-weight:bold;
  font-size:18px;
  line-height:22px;
  
  align-items:center;
  text-align:center;
}

.icon_star{
  height:44px;
  width:44px;
   margin-right:8px;
}

.text_pokename{
  margin:0;
}

.pokedetails{
  height:60px;
}

.text_pokename{
 margin-left:20px;
 height:26px;
 font-family:'Lato';
 font-style:normal;
 font-weight:500;
 font-size:22px;
 line-height:26px;
 color:#353535;
}
</style>