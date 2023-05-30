<template>
    <div class="container">
      <h2>Actualizar Usuario</h2>
      <form @submit.prevent="updateUser" enctype="multipart/form-data">
        <div class="form-group">
          <label for="id_usuario">ID Usuario:</label>
          <input type="number" id="id_usuario" class="form-control" v-model="id_usuario" required>
        </div>
        <div class="form-group">
          <label for="nickname">Nickname:</label>
          <input type="text" id="nickname" class="form-control" v-model="nickname" required>
        </div>
        <div class="form-group">
          <label for="password">Contraseña:</label>
          <input type="password" id="password" class="form-control" v-model="password" required>
        </div>
        <div class="form-group">
          <label for="nombre">Nombre:</label>
          <input type="text" id="nombre" class="form-control" v-model="nombre" required>
        </div>
        <div class="form-group">
          <label for="apellido">Apellido:</label>
          <input type="text" id="apellido" class="form-control" v-model="apellido" required>
        </div>
        <div class="form-group">
          <label for="edad">Edad:</label>
          <input type="number" id="edad" class="form-control" v-model="edad" required>
        </div>
        <div class="form-group">
          <label for="genero">Género:</label>
          <select id="genero" class="form-control" v-model="genero" required>
            <option value="masculino">Masculino</option>
            <option value="femenino">Femenino</option>
          </select>
        </div>
        <div class="form-group">
          <label for="correo_electronico">Correo Electrónico:</label>
          <input type="email" id="correo_electronico" class="form-control" v-model="correoElectronico" required>
        </div>
        <div class="form-group">
          <label for="telefono">Teléfono:</label>
          <input type="text" id="telefono" class="form-control" v-model="telefono" required>
        </div>
        <div class="form-group">
          <label for="direccion">Dirección:</label>
          <input type="text" id="direccion" class="form-control" v-model="direccion" required>
        </div>
        <div class="form-group">
          <label for="foto">Foto:</label>
          <input type="file" id="foto" class="form-control-file" @change="onFileChange" accept="image/*" required>
        </div>
        <button type="submit" class="btn btn-primary">Actualizar Usuario</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        id_usuario: null,
        nickname: '',
        password: '',
        nombre: '',
        apellido: '',
        edad: 0,
        genero: 'masculino',
        correoElectronico: '',
        telefono: '',
        direccion: '',
        foto: null
      };
    },
    methods: {
      onFileChange(event) {
        this.foto = event.target.files[0];
      },
      updateUser() {
        const formData = new FormData();
        formData.append('id_usuario', this.id_usuario);
        formData.append('nickname', this.nickname);
        formData.append('password', this.password);
        formData.append('nombre', this.nombre);
        formData.append('apellido', this.apellido);
        formData.append('edad', this.edad);
        formData.append('genero', this.genero);
        formData.append('correo_electronico', this.correoElectronico);
        formData.append('telefono', this.telefono);
        formData.append('direccion', this.direccion);
        formData.append('foto', this.foto);
        axios.patch('http://127.0.0.1:5050/user', formData)
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