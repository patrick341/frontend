<template>
    <div>
      <!-- Formulario para crear un usuario -->
      <form @submit="crearUsuario">
        <div class="mb-3">
          <label for="nickname" class="form-label">Nickname</label>
          <input type="text" class="form-control" id="nickname" v-model="usuario.nickname" required>
        </div>
        <!-- Resto de campos del formulario (password, nombre, apellido, etc.) -->
        
        <div class="mb-3">
          <label for="foto" class="form-label">Foto</label>
          <input type="file" class="form-control" id="foto" @change="handleFileChange" required>
        </div>
        
        <button type="submit" class="btn btn-primary">Crear usuario</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        usuario: {
          nickname: '',
          password: '',
          nombre: '',
          apellido: '',
          // Resto de campos del usuario
          foto: null, // Propiedad para almacenar la imagen seleccionada
        },
      };
    },
    methods: {
      crearUsuario() {
        // Crea un objeto FormData para enviar los datos y la imagen al backend
        const formData = new FormData();
        formData.append('nickname', this.usuario.nickname);
        formData.append('password', this.usuario.password);
        formData.append('nombre', this.usuario.nombre);
        formData.append('apellido', this.usuario.apellido);
        // Agrega el resto de campos del usuario
        
        formData.append('foto', this.usuario.foto); // Agrega la imagen al FormData
        
        // Realiza una solicitud POST al backend Flask
        axios
          .post('http://127.0.0.1:5050/users', formData, {
            headers: {
              'Content-Type': 'multipart/form-data',
            },
          })
          .then(response => {
            // Maneja la respuesta del backend (puede mostrar un mensaje de éxito, etc.)
            console.log(response.data);
          })
          .catch(error => {
            // Maneja los errores de la solicitud
            console.error(error);
          });
      },
      handleFileChange(event) {
        // Maneja el cambio de la imagen seleccionada
        this.usuario.foto = event.target.files[0];
      },
    },
  };
  </script>
  