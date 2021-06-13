<template>
  <div id="app">
    <Loading/>
    <ListaPokemon/>
  </div>
</template>


<script>
import Loading from '../components/loading.vue'
import ListaPokemon from '../components/listaPokemon.vue'

export default {
  name: 'App',
  components: {
    Loading,
    ListaPokemon
  }
}
</script>