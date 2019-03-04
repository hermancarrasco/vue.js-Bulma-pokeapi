<template>
  <div class="home">
    <div class="container spa">
      <br>
    <pokemons></pokemons>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import pokemons from '@/components/pokemons.vue'

export default {
  name: 'home',
  components: {
    pokemons
  }
}
</script>
