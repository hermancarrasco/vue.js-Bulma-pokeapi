<template>
  <div>
    <div class="columns is-multiline">
      <div class="column is-3" v-for="(poke, index) in pokes" :key="index">
        <div class="card">
          <div class="card-image">
            <figure class="image is-4by3">
              <img :src="imagen(index)" :alt="poke.name">
            </figure>
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content has-text-centered">
                <p class="title is-4 is-capitalized">{{poke.name}}</p>
              </div>
            </div>
            <div class="has-text-centered">
              <router-link :to="ruta(poke.name)" class="button is-primary is-outlined is-large">Ver Detalles</router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="columns">
      <div class="column has-text-centered">
        <hr>
        <a class="button is-primary is-outlined is-large" v-on:click="cargarMas()">Ver Más</a>
      </div>
    </div>

  </div>
</template>

<script>

  import Axios from 'axios';

export default {
  name: 'pokemons',
  data() {
    return {
      pokes : '',
      next: ''
    }
  },
  created(){
    Axios.get('https://pokeapi.co/api/v2/pokemon').then(res=>{
      console.log(res);
      this.next = res.data.next;
      this.pokes = res.data.results;
    })

  },
  methods:{
    imagen(num){
      return "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/"+ parseInt(num+1) +".png";
    },
    ruta(nom){
      return '/pokemon/'+ nom;
    },
    cargarMas(){
      Axios.get(this.next).then(res=>{
        console.log(res);
        this.next = res.data.next;
        this.pokes = [...this.pokes, ...res.data.results];
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
