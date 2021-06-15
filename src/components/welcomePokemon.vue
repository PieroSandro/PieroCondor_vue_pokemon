<template>
  
   <div class="container">
   
    <div class="frame_pk">
      <img id="img_pikachu" src="../assets/img/pikachu.png">
    </div>
       
    
    <p id="title_pk">Welcome to Pokédex</p>

    <div class="parag_class">
     <!-- <p id="parag_pk">
        The digital encyclopedia created by Professor Oak is an invaluable tool to 
        Trainers in the Pokémon world</p>-->
        The digital encyclopedia created by Professor Oak is an invaluable tool to 
        Trainers in the Pokémon world
    </div>
    <router-link to="pageone"><button id="red_button" type="button" class="btn">Get started</button></router-link>
    <!--<p id="parag_pk">The digital encyclopedia</p>-->
    
    </div>
    
  

</template>


<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios,axios)


export default {
  name: 'WelcomePokemon',
mounted(){
    Vue.axios.get('https://pokeapi.co/api/v2/pokemon/1')
    .then((resp)=>{
        console.warn(resp.data)
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

#img_pikachu{
max-width:100%;
max-height:100%;
}

.frame_pk{
  /*  display: block;
    margin-right: auto;
    margin-left:auto;*/
  margin-top:70px;
  height:288px;
  width:325px;
  /*border-style: solid;
  border-width:1px;
  border-color:red;
 border-bottom:1px solid rgba(0,0,0,0.1);*/
  cursor:pointer;
  overflow:hidden;
}

#title_pk{
  margin-top:60px;
  font-family:'Lato';
  font-style: normal;
  font-weight: bold;

  font-size:26px;
  line-height:31px;
  margin-bottom:0px;
}

#red_button{
   margin-top:50px;

   border-radius:60px;
   background-color:#F22539;

    height:44px;
  width:131px;

  color:#FFFFFF;

  font-family:'Lato';
  font-style: normal;
  font-weight: bold;

  font-size:18px;
  line-height:22px;
}

@media screen and (max-width: 575px) {
  
.parag_class{
  margin-top:30px;
  height:82px;
  width:315px;
 /* border-style: solid;
  border-width:1px;
  border-color:red;*/
 /*border-bottom:1px solid rgba(0,0,0,0.1);*/
  overflow:hidden;

   
  font-family:'Lato';
  font-style: normal;
  font-weight: 500;

  font-size:18px;
  line-height:150%;
  text-align:center;
  color:#5E5E5E;
}
        
}

@media screen and (min-width: 576px) {
.parag_class{
  margin-top:30px;
  height:54px;
  width:570px;
  /*border-style: solid;
  border-width:1px;
  border-color:red;*/
 /*border-bottom:1px solid rgba(0,0,0,0.1);*/
  overflow:hidden;


   
  font-family:'Lato';
  font-style: normal;
  font-weight: 500;

  font-size:18px;
  line-height:150%;
  text-align:center;
  color:#5E5E5E;
  /*margin-bottom:0px;*/
  
}
        
}

</style>