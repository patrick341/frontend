<template>
  <div>
    <div v-for="user in mappedData" :key="user.id_usuario">
      <p>Nickname: {{ user.nickname }}</p>
      <p>Password: {{ user.password }}</p>
      <p>Apellido: {{ user.apellido }}</p>
      <p>Nombre: {{ user.nombre }}</p>
      <p>Genero: {{ user.genero }}</p>
      <p>Id_Usuario: {{ user.id_usuario }}</p>
      <p>Vector_Foto: {{ user.vector_foto }}</p>
      <p>Direccion: {{ user.direccion }}</p>
      <p>Dni: {{ user.dni }}</p>
      <p>Edad: {{ user.edad }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      responseData: null
    };
  },
  created() {
    axios.post('http://127.0.0.1:5050/users')
      .then(response => {
        this.responseData = response.data;
      })
      .catch(error => {
        // Manejar el error
        console.error(error);
      });
  },
  computed: {
    mappedData() {
      if (this.responseData) {
        return this.responseData.map(user => ({
          nickname: user.nickname,
          password: user.password,
          apellido: user.apellido,
          nombre: user.nombre,
          edad: user.edad,
          foto:user.foto,
          telefono: user.telefono,
          id_usuario: user.id_usuario,
          vector_foto: user.vector_foto,
          genero: user.genero

        }));
      }
      return [];
    }
  }
}
</script>
