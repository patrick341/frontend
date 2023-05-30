<template>
    <div>
      <h2>Insertar Usuario</h2>
      <b-form @submit.prevent="insertUser" enctype="multipart/form-data">
        <b-form-group id="nickname" label="Nickname:" label-for="nickname-input" label-cols-sm="3">
          <b-form-input id="nickname-input" v-model="nickname" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="password" label="Contraseña:" label-for="password-input" label-cols-sm="3">
          <b-form-input id="password-input" type="password" v-model="password" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="nombre" label="Nombre:" label-for="nombre-input" label-cols-sm="3">
          <b-form-input id="nombre-input" v-model="nombre" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="apellido" label="Apellido:" label-for="apellido-input" label-cols-sm="3">
          <b-form-input id="apellido-input" v-model="apellido" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="edad" label="Edad:" label-for="edad-input" label-cols-sm="3">
          <b-form-input id="edad-input" type="number" v-model="edad" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="genero" label="Género:" label-for="genero-select" label-cols-sm="3">
          <b-form-select id="genero-select" v-model="genero" required>
            <option value="M">Masculino</option>
            <option value="F">Femenino</option>
          </b-form-select>
        </b-form-group>
  
        <b-form-group id="correo" label="Correo Electrónico:" label-for="correo-input" label-cols-sm="3">
          <b-form-input id="correo-input" type="email" v-model="correo" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="telefono" label="Teléfono:" label-for="telefono-input" label-cols-sm="3">
          <b-form-input id="telefono-input" type="tel" v-model="telefono" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="direccion" label="Dirección:" label-for="direccion-input" label-cols-sm="3">
          <b-form-input id="direccion-input" v-model="direccion" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="dni" label="DNI:" label-for="dni-input" label-cols-sm="3">
          <b-form-input id="dni-input" v-model="dni" required></b-form-input>
        </b-form-group>
  
        <b-form-group id="foto" label="Foto:" label-for="foto-input" label-cols-sm="3">
          <b-form-file id="foto-input" v-model="foto" required></b-form-file>
        </b-form-group>
  
        <b-button type="submit" variant="primary">Insertar Usuario</b-button>
      </b-form>
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
  