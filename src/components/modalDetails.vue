<template>
    <div class="container">
     <div v-if="show_modal" id="backgroundDark">
  <div id="windowModal" class="card">
      <img @click="show_modal=false" id="close_iconpoke" src="../assets/img/close_icon.png">
    <img
    src="../assets/img/bg_lake.png"
    class="card-img-top"
    alt="lake"
  />
  <div class="card-img-overlay">
      <div class="row" id="row_image">
    <!--<h5 class="card-title">Card title</h5>
    <p class="card-text">
      This is a wider card with supporting text below as a natural lead-in to additional
      content. This content is a little bit longer.
    </p>
    <p class="card-text">Last updated 3 mins ago</p>-->
    
    <div class="d-flex justify-content-center">
        <div id="frame_pokemon">
<img id="img_pokemonfront" v-bind:src="imgPk">
        </div>
    </div>
    </div>
  </div>
       {{namePk}}<br>
      {{heightPk}}<br>
      {{weightPk}}<br>
       {{typesPk}}<br>
     <!--  <img @click="show_modal=false" style="size:26px;" src="../assets/img/close_icon.png">-->
  </div>
    </div>
    </div>
  
  <!-- -->

</template>


<script>
import {bus} from '../main';
export default {
  name: 'modalDetails',
  data(){
      return{
          namePk:'',
          heightPk:'',
          weightPk:'',
          typesPk:'',
          types_array:[],
          incrementNum:0,
          show_modal:false,
          imgPk:'',
      }
  },
  created(){
    bus.$on('busDataPokemon',(data)=>{
        this.show_modal=true;
      this.namePk=data.namePokemon;
      this.heightPk=data.heightPokemon;
      this.weightPk=data.weightPokemon;
       this.typesPk=data.typesPokemon;
       this.imgPk=data.imgPokemon;
       this.types_array=[];
      // console.log('tu nombre es '+this.namePk)
      for(this.incrementNum=0;this.incrementNum<this.typesPk.length;this.incrementNum++){
           this.types_array.push(this.typesPk[this.incrementNum].type.name)
          }
          console.log('arreglo tipos: '+this.types_array)
  
    })

  }

}
</script>
<style>
   #backgroundDark{
   z-index:100; 
  height:100vh;
  width:100%; 
  position:fixed;
  top:0;
  left:0; 
  background-color:rgba(0,0,0,0.6);
  display:flex;
  justify-content:center;
  align-items:center;
   }

   @media screen and (max-width: 575px) {
       #windowModal{
           width:315px;
           height:506px;
           border-radius:5px;
           background-color:#FFFFFF;
       }
   }

   @media screen and (min-width: 576px) {
       #windowModal{
            width:570px;
           height:506px;
            border-radius:5px;
             background-color:#FFFFFF;
       }
   }

   .card-img-top{
       height:220px;
      /* max-width: none;*/
   }

   #windowModal{
       border: none;
   }

   
#frame_pokemon{
 height:180px;
  width:180px;
  overflow:hidden;
}

.card-img-overlay{
    padding:0px;
}

#row_image{
    width:100%; 
   
    margin-top:20px;
}

#img_pokemonfront{
    height:100%; 
    width:100%;
}

#close_iconpoke{
    z-index: 9; 
    position: absolute; 
    top:15px; 
    right:15px; 
    height:26px;
    width:26px; 
    cursor:pointer;
}
</style>