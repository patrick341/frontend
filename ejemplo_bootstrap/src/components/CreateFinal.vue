<template>
    <div>
      <h2>Insertar Usuario</h2>
      <form @submit.prevent="insertUser" enctype="multipart/form-data">
        <label for="nickname">Nickname:</label>
        <input type="text" id="nickname" v-model="nickname" required><br>
  
        <!-- Resto de los campos del formulario -->
  
        <label for="foto">Foto:</label>
        <vue-upload-component
          ref="fotoUploader"
          id="foto"
          @input="handleFileChange"
          accept="image/*"
          required
        ></vue-upload-component>
  
        <button type="submit">Insertar Usuario</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import VueUploadComponent from 'vue-upload-component';
  
  export default {
    components: {
      VueUploadComponent
    },
    data() {
      return {
        nickname: '',
        password: '',
        nombre: '',
        apellido: '',
        edad: null,
        genero: '',
        correo: '',
        telefono: '',
        direccion: '',
        dni: '',
        foto: null
      };
    },
    methods: {
      handleFileChange(file) {
        this.foto = file;
      },
      insertUser() {
        const formData = new FormData();
        formData.append('nickname', this.nickname);
        formData.append('password', this.password);
        formData.append('nombre', this.nombre);
        formData.append('apellido', this.apellido);
        formData.append('edad', this.edad);
        formData.append('genero', this.genero);
        formData.append('correo_electronico', this.correo);
        formData.append('telefono', this.telefono);
        formData.append('direccion', this.direccion);
        formData.append('dni', this.dni);
        formData.append('foto', this.foto);
  
        // Realizar la solicitud POST utilizando Axios
        axios
          .post('http://127.0.0.1:5050/usuario', formData)
          .then(response => {
            console.log(response.data);
            // Realizar acciones adicionales después de insertar el usuario
          })
          .catch(error => {
            console.error(error);
            // Manejar errores en caso de que la solicitud falle
          });
      }
    }
  };
  </script>
  
  
  
  