<template>
  <div class="container">
    <br>
    <router-link to="/" class="button is-primary is-outlined is-large">Atras</router-link>

    <div class="columns is-centered">
      <div class="column is-half is-4">
        <div v-if="!pokemon" class="has-text-centered">Cargando</div>

        <div class="card" v-if="pokemon">
          <div class="card-image">
            <figure class="image is-4by3" v-if="pokemon.sprites">
              <img :src="pokemon.sprites.front_default" :alt="pokemon.name">
            </figure>
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content has-text-centered">
                <p class="title is-4 is-capitalized">{{pokemon.name}}</p>
              </div>
            </div>

            <aside class="menu">
              <p class="menu-label">
                Información
              </p>
              <ul class="menu-list">
                <li v-if="pokemon.height < 10">
                  <a><span>Estatura</span>: <span class="is-pulled-right">{{pokemon.height * 10}} Centimetros</span>
                  </a>
                </li>
                <li v-if="pokemon.height > 9">
                  <a><span>Estatura</span>: <span class="is-pulled-right">{{pokemon.height / 10}} Metros</span> </a>
                </li>
                <li><a><span>Peso</span> : <span class="is-pulled-right">{{pokemon.weight / 10}} Kilos</span> </a></li>
              </ul>
              <ul class="menu-list">
                <li>
                  <a class="is-active">Tipos</a>
                  <ul>
                    <li v-for="item in pokemon.types" :key="item.type.name"><a class="is-capitalized">{{item.type.name}}</a></li>
                  </ul>
                </li>
              </ul>
            </aside>
          </div>
        </div>


      </div>

    </div>

  </div>
</template>

<script>

  import Axios from 'axios';

export default {
  name: 'pokemonComp',
  props: {
    msg: String
  },
  data() {
    return {
      pokemon : ''
    }
  },
  mounted(){
    const id = this.$route.params.id;
    Axios.get('https://pokeapi.co/api/v2/pokemon/'+ id).then(res=>{
      console.log(res);
      this.pokemon = res.data;
    })

  },
  methods:{
    imagen(num){
      return "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/"+ parseInt(num+1) +".png";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
