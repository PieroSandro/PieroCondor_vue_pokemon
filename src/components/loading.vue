<template>
  <transition name="fade">
      <div v-if="show" class="preloader">
          <div class="logo">
              <img id="img_pokeball" src="../assets/img/pokeball.png">
          </div>
         <!-- <p>Cargando</p>-->
      </div>
  </transition>
</template>

<script>
import {bus} from '../main';
export default {
  name: 'Loading',
  data(){
      return{
          show:true,
          bus_datainfo:false,
      }
  },
  mounted(){
     this.showToggle();
  },
  methods:{
      showToggle(){
          setTimeout(() => {
              this.show=false;
              this.bus_datainfo=true;
              console.log(this.bus_datainfo)
              bus.$emit('sendData',this.bus_datainfo);
          }, 3000);
          
      }
  }
}
</script>

<style>
.preloader{
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    position:absolute;
    width:100%;
    height:100%;
    background-color:#F9F9F9;
    z-index:9999;
}

.logo{
   /* width:12.5rem;
    height:12.5rem;
    background-image: url('../assets/img/pokeball.png');
    background-repeat:no-repeat;*/
    height:106px;
  width:106px;
  /*border-style: solid;
  border-width:1px;
  border-color:red;
 border-bottom:1px solid rgba(0,0,0,0.1);*/
  overflow:hidden;
}


#img_pokeball{
max-width:100%;
max-height:100%;
}

/*
p{
    font:600 1.5rem;
    margin-top:1rem;
}
*/
.fade-enter-active, .fade-leave-active{
    transition:opacity 3s;
}

.logo{
    animation-name: scaleOut;
    animation-duration: 3s;
}

/*
p{
    animation-name: scaleOut;
    animation-duration: 2s;
}
*/
.fade-enter, .fade-leave-to{
    opacity:0;
}

@keyframes scaleOut{
    0%
    {
        transform: scale(1);
    }
    100%
    {
        transform: scale(0);
    }
}
</style>