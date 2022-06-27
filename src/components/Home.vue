
<template>

<input type="text"  name="" v-model="nome" id="">
<input type="button" value="Busca" v-on:click="retornaPokemon()">
<div v-if="pokemonSelecionado.data==undefined">

    <p v-for="item in response.data.results"><input  type="button" v-on:click="selecionaPokemon(item.url)" v-bind:value="item.name"/> </p>
</div>
<div  v-else>


<div class="card m-auto " style="width: 14rem;">
  <img class="card-img-top" v-bind:src="pokemonSelecionado.data.sprites.front_default"  alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">{{pokemonSelecionado.data.name}} </h5>
    <p class="card-text">hp:{{pokemonSelecionado.data.stats[0].base_stat}}   
    defesa:{{pokemonSelecionado.data.stats[1].base_stat}}   </p>
    <p class="card-text">ataque:{{pokemonSelecionado.data.stats[2].base_stat}}
    velocidade:{{pokemonSelecionado.data.stats[5].base_stat}}
       </p>
    <p class="card-text">defesa especial:{{pokemonSelecionado.data.stats[4].base_stat}}   </p>
    <p class="card-text">ataque especial:{{pokemonSelecionado.data.stats[3].base_stat}}   </p>
    
  </div>
</div>


</div>





</template>



<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';



export default defineComponent({
  name: 'Home',
  data() {
    return { nome: "",response:{data:{count:null,results:[]}} ,pokemonSelecionado:{}}
  },
  methods:{
      selecionaPokemon(url:string){
          axios.get(url).then((response)=>{
              console.log(response);
              this.pokemonSelecionado=response;
          })


      },
retornaPokemon(){
axios.get('https://pokeapi.co/api/v2/pokemon/'+this.nome).then((response)=>{
   console.log(response);
   if(response.data.count==undefined){
       this.pokemonSelecionado=response;
   }else{

   this.response=response;
   this.pokemonSelecionado={};
       
   }
   return response; 
    }).catch((e)=>{
        return e;
    })

}

  }
});
</script>