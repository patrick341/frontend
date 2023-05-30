<template>
    <div>
      <h2>Insertar Usuario</h2>
      <form @submit.prevent="insertUser" enctype="multipart/form-data">
        <label for="nickname">Nickname:</label>
        <input type="text" id="nickname" v-model="nickname" required><br>
  
        <label for="password">Contraseña:</label>
        <input type="password" id="password" v-model="password" required><br>
  
        <label for="nombre">Nombre:</label>
        <input type="text" id="nombre" v-model="nombre" required><br>
  
        <label for="apellido">Apellido:</label>
        <input type="text" id="apellido" v-model="apellido" required><br>
  
        <label for="edad">Edad:</label>
        <input type="number" id="edad" v-model="edad" required><br>
  
        <label for="genero">Género:</label>
        <select id="genero" v-model="genero" required>
          <option value="M">Masculino</option>
          <option value="F">Femenino</option>
        </select><br>
  
        <label for="correo">Correo Electrónico:</label>
        <input type="email" id="correo" v-model="correo" required><br>
  
        <label for="telefono">Teléfono:</label>
        <input type="tel" id="telefono" v-model="telefono" required><br>
  
        <label for="direccion">Dirección:</label>
        <input type="text" id="direccion" v-model="direccion" required><br>
  
        <label for="dni">DNI:</label>
        <input type="text" id="dni" v-model="dni" required><br>
  
        <label for="foto">Foto:</label>
        <input type="file" id="foto" @change="handleFileChange" required><br>
  
        <button type="submit">Insertar Usuario</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
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
      handleFileChange(event) {
        this.foto = event.target.files[0];
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
        axios.post('http://127.0.0.1:5050/usuario', formData)
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
  