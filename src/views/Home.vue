<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>Id</th>
          <th>Nombre</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pelicula in peliculas" :key="pelicula.id">
          <td>{{pelicula.id}}</td>
          <td>{{pelicula.nombre}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      peliculas: [],
      api: 'http://localhost/codeigniter/index.php/welcome'
    }
  },
  mounted() {
    this.obtenerPeliculas()
  },
  methods: {
    obtenerPeliculas() {
      this.axios.get(this.api+'/peliculas').then(response => {
        this.peliculas = response.data
        console.log(this.peliculas)
      })
    }
  }
}
</script>
