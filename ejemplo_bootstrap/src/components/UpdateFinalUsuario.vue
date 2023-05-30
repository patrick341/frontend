<template>
    
    <div class="table-container">
      <h2>Mostrar Usuario</h2>
      <b-table responsive striped hover :items="mappedData" class="custom-table">
        <template #cell(actions)="row">
          <button class="btn btn-danger">Borrar</button>
          <button class="btn btn-primary">Actualizar</button>
          <b-button @click="updateUser(row.item.id_usuario)">Actualizar</b-button>
        </template>
      </b-table>
    </div>
  </template>
  
  <style>
  .table-container {
    max-height: 400px; /* Ajusta la altura máxima según tus necesidades */
    overflow-y: auto;
    overflow-x: auto;
  }
  
  /* Resto del estilo de la tabla */
  .custom-table {
    font-family: 'Arial', sans-serif;
    font-size: 14px;
    color: #333;
    border-collapse: separate;
    border-spacing: 0 10px;
    white-space: nowrap; /* Evita el ajuste de texto al contenido */
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
            foto: user.foto,
            telefono: user.telefono,
            id_usuario: user.id_usuario,
            vector_foto: user.vector_foto,
            genero: user.genero,
            email:user.correo,
            direccion: user.direccion,
            dni: user.dni
          }));
        }
        return [];
      }
    },
    methods: {
      updateUser(id_usuario) {
        // Aquí puedes agregar la lógica para actualizar el usuario con el id proporcionado
        
        

        //console.log('Actualizar usuario:', id_usuario);
        const formData = new FormData();
        formData.append('id_usuario', id_usuario);
    // Aquí puedes agregar los campos adicionales que deseas actualizar en el usuario

        axios.patch('http://127.0.0.1:5050/user', formData)
            .then(response => {
                console.log('Usuario actualizado:', response.data);
        // Realizar acciones adicionales después de actualizar el usuario
        })
        .catch(error => {
            console.error('Error al actualizar el usuario:', error);
        // Manejar errores en caso de que la solicitud falle
        });
    
    
    }
    }
  }
  </script>


