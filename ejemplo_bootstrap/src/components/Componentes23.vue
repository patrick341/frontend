<template>
    <div>
      <b-table striped hover :items="mappedData" class="custom-table"></b-table>
    </div>
  </template>
  
  <style>
  .custom-table {
    font-family: 'Arial', sans-serif;
    font-size: 14px;
    color: #333;
    border-collapse: separate;
    border-spacing: 0 10px;
  }
  
  .custom-table thead th {
    background-color: #343a40;
    color: #fff;
    font-weight: bold;
    padding: 10px;
  }
  
  .custom-table tbody td {
    padding: 10px;
  }
  
  .custom-table tbody tr {
    background-color: #f8f9fa;
  }
  
  .custom-table tbody tr:nth-child(even) {
    background-color: #f2f2f2;
  }
  
  .custom-table tbody tr:hover {
    background-color: #e2e6ea;
  }
  </style>
  
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
  
  