<template>
  
   <div class="container">
   
    <div class="frame_pk"></div>
       
    
    <p id="title_pk">Welcome to Pokédex</p>

    <p id="parag_pk">The digital encyclopedia</p>
    
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


@media screen and (max-width: 575px) {
.frame_pk{
  margin-top:70px;
  height:288px;
  width:325px;
  border-style: solid;
  border-width:1px;
  border-color:red;
 /*border-bottom:1px solid rgba(0,0,0,0.1);*/
  cursor:pointer;
  overflow:hidden;
}

#title_pk{

}
        
}

@media screen and (min-width: 576px) {
.frame_pk{
  /*  display: block;
    margin-right: auto;
    margin-left:auto;*/
  margin-top:70px;
  height:288px;
  width:325px;
  border-style: solid;
  border-width:1px;
  border-color:red;
 /*border-bottom:1px solid rgba(0,0,0,0.1);*/
  cursor:pointer;
  overflow:hidden;
}

#title_pk{
   /* display: block;
    margin-right: auto;
    margin-left:auto;*/
}
        
}

</style>