<template>
    <div>
      <h2>Eliminar Usuario</h2>
      <form @submit.prevent="deleteUser">
        <div>
          <label for="id_usuario">ID Usuario:</label>
          <input type="number" id="id_usuario" v-model="idUsuario" required>
        </div>
        <button type="submit">Eliminar Usuario</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        idUsuario: null
      };
    },
    methods: {
      deleteUser() {
        axios.delete('http://127.0.0.1:5050/user', { data: { id_usuario: this.idUsuario } })
          .then(response => {
            // Manejar la respuesta de la API
            console.log(response.data);
          })
          .catch(error => {
            // Manejar el error de la API
            console.error(error);
          });
      }
    }
  };
  </script>
  