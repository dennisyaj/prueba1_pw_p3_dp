<template >
    <div class="letras">
        <h1>Puntaje:</h1>
        <h1>Intento:</h1>
    </div>
    <div class="container">
        <PokemonImg :id="rendePoke[0]" :visible="vis"></PokemonImg>
        <PokemonImg :id="rendePoke[1]"></PokemonImg>
        <PokemonImg :id="rendePoke[2]"></PokemonImg>
    </div>
    <div>
        <h1>haz utilixado tus intentos</h1>
        <h2>El jhuego ha terminado, intentalo nuevamente</h2>
    </div>
    <div>
        
    </div>
    <button v-on:click="jugar">Jugar</button>

</template>
<script>
import PokemonImg from '@/components/PokemonImg.vue';
export default {
    data() {
        return {
            todos: [12, 15, 49, 1],
            rendePoke: [1, 2, 3],
            nombrePoke: [],
            vis: true,
            mensaje: false
        }
    },
    components: {
        PokemonImg
    },
    methods: {
        jugar() {
            this.listaPokemon()
            this.vis = false
            this.obtenerNombre()

        }
        ,
        async obtenerNombre() {
            const { name } = await fetch('https://pokeapi.co/api/v2/pokemon/' + this.rendePoke[0] + '').then(r => r.json())
            this.nombre = name
        },
        listaPokemon() {

            this.rendePoke[0] = this.todos.findIndex(this.crearRandom())
            this.rendePoke[1] = this.todos.findIndex(this.crearRandom())
            this.rendePoke[2] = this.todos.findIndex(this.crearRandom())

        }, crearRandom() {
            return Math.floor(Math.random() * 3);
        },
        puntos() {
            if (this.rendePoke[0] == this.rendePoke[1]) {

            }
        }



    }, computed: {


    }
}
</script>
<style >
.container {
    display: grid;
    grid-template-columns: auto auto auto;

}

.letras {
    display: grid;
    grid-template-columns: auto auto;
}
</style>