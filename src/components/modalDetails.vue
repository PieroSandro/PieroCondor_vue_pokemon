<template>
    <div class="container">
     <div v-if="show_modal" id="backgroundDark">
  <div @click="show_modal=false" id="windowModal" class="card">
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
      }
  },
  created(){
    bus.$on('busDataPokemon',(data)=>{
        this.show_modal=true;
      this.namePk=data.namePokemon;
      this.heightPk=data.heightPokemon;
      this.weightPk=data.weightPokemon;
       this.typesPk=data.typesPokemon;
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
</style>