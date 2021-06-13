<template>
  <transition name="fade">
      <div v-if="show" class="preloader">
          <div class="logo"></div>
         <!-- <p>Cargando</p>-->
      </div>
  </transition>
</template>

<script>
export default {
  name: 'Loading',
  data(){
      return{
          show:true
      }
  },
  mounted(){
      this.showToggle();
  },
  methods:{
      showToggle(){
          setTimeout(() => {
              this.show=false;
          }, 2000);
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
    background-color:white;
    z-index:9999;
}

.logo{
    width:12.5rem;
    height:12.5rem;
    background-image: url('../assets/img/pokeball.png');
    background-repeat:no-repeat;
}
/*
p{
    font:600 1.5rem;
    margin-top:1rem;
}
*/
.fade-enter-active, .fade-leave-active{
    transition:opacity 2s;
}

.logo{
    animation-name: scaleOut;
    animation-duration: 2s;
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