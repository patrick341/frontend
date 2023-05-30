<template>
    <div class="container">
      <h2>Eliminar Usuario</h2>
      <form @submit.prevent="deleteUser" class="form-group">
        <div>
          <label for="id_usuario">ID Usuario:</label>
          <input type="number" id="id_usuario" v-model="idUsuario" required class="form-control">
        </div>
        <button type="submit" class="btn btn-danger">Eliminar Usuario</button>
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
  
  <style scoped>
  .container {
    max-width: 500px;
    margin: auto;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  </style>
  