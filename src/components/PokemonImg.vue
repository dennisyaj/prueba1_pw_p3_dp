<template >
    <div>
        <img class="cuadrado-negro"  v-if="visible" src="https://cdn.icon-icons.com/icons2/1238/PNG/512/blacksquare_83753.png"
            alt="no se encontro el archivo">
        <img v-bind:src="pokemon" alt="no se cargo">
        <h1>{{ titulo }}</h1>
    </div>
</template>
<script>
export default {
    data() {

    },
    props: {
        id: Number,
        titulo: String,
        visible: Boolean
    }, methods: {

    }, computed: {
        pokemon() {
            return "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/" + this.id + ".svg"
        }
    }
}
</script>
<style >
.cuadrado-negro {
    position: absolute;
    filter: brightness(0);

}

img {
    height: 30%;
}
</style>