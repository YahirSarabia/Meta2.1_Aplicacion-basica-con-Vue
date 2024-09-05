<script setup>
    import { ref, onMounted} from 'vue';
    const datos = ref(null);
    onMounted( async() => {
        const response = await fetch("https://dummyapi.online/api/movies");
        datos.value = await response.json();
    });

    const titulo = ref('Titulo: ')
    function cambiarTitulo( nombre ){
        titulo.value = `Titulo: ${nombre}`
    }
</script>

<template>
    <div>
        <h1> {{ titulo }} </h1>
        <table v-if="datos" border="1">
            <caption style="font-size:30px;">Películas</caption>
            <tr>
                <th>Título</th>
                <th>Calificación</th>
                <th>IMDB</th>
            </tr>
            <tr v-for="movie in datos" :key="movie.id">
                <td @click="cambiarTitulo(movie.movie)">{{ movie.movie }}</td>
                <td>{{ movie.rating }}</td>
                <td><a :href="movie.imdb_url" target="_blank"> {{movie.imdb_url}} </a></td>
            </tr>
        </table>
        <p v-else>Cargando datos...</p>
    </div>
</template>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th, td {
  padding: 10px;
  text-align: left;
  color: white;
}

th {
  background-color: #42b983;
  color: white;
}

a {
  color: #42b983;
  text-decoration: none;
}
</style>