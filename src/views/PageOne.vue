<template>
  <div id="app">
    <Loading/>
    <ListaPokemon/>
    <ModalDetails/>
  </div>
</template>


<script>
import Loading from '../components/loading.vue'
import ListaPokemon from '../components/listaPokemon.vue'
import ModalDetails from '../components/modalDetails.vue'

export default {
  name: 'App',
  components: {
    Loading,
    ListaPokemon,
    ModalDetails
  }
}
</script>