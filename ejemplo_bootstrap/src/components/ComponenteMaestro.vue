<template>
    <v-app>
      <v-main class="fondo3">
        <v-card class="ma-auto mt-10" height="620" width="374">
          <v-img
            height="30%"
            src="https://thumbs.dreamstime.com/b/plaza-de-armas-arequipa-per%C3%BA-49441219.jpg"
          ></v-img>
          <v-card-title class="mt-0 mb-0 justify-center">
            BuResol v1.0
          </v-card-title>
          <v-card-title class="amber--text justify-center">Usuarios</v-card-title>
  
          <v-form class="mt-0 ml-5 mr-5" ref="forms" v-model="valid" lazy-validation>
            <v-text-field v-model="crearUsuario.nickname" label="Nickname"></v-text-field>
            <v-text-field v-model="crearUsuario.password" label="Password" type="password"></v-text-field>
            <v-text-field v-model="crearUsuario.nombre" label="Nombre"></v-text-field>
            <v-text-field v-model="crearUsuario.apellido" label="Apellido" ></v-text-field>
            <v-text-field v-model="crearUsuario.genero" label="Genero"></v-text-field>
            <v-text-field v-model="crearUsuario.correo_electronico" label="Correo Electronico"></v-text-field>
            <v-text-field v-model="crearUsuario.telefono" label="Telefono"></v-text-field>
            <v-text-field v-model="crearUsuario.direccion" label="Direccion"></v-text-field>
            <v-text-field v-model="crearUsuario.dni" label="DNI"></v-text-field>
            <v-text-field v-model="crearUsuario.foto" label="Foto"></v-text-field>
            <v-text-field v-model="crearUsuario.edad" label="Edad"></v-text-field>

            <v-btn :disabled="!valid" color="amber" block class="white--text" @click="crearUsuarioAPI">
              Crear Usuario
            </v-btn>
  
            <v-divider class="my-2"></v-divider>
  
            <v-text-field v-model="eliminarUsuario.nickname" label="Nickname a eliminar"></v-text-field>
  
            <v-btn :disabled="!valid" color="red" block class="white--text" @click="eliminarUsuarioAPI">
              Eliminar Usuario
            </v-btn>
          </v-form>
        </v-card>
      </v-main>
    </v-app>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data: () => ({
      config_request: {
        "Content-Type": "application/json",
        "Access-Control-Allow-Origin": "*",
      },
      valid: true,
      crearUsuario: {
        nickname: "",
        password: "",
        nombre:"",
        apellido:"",
        genero: "",
        correo_electronico: "",
        telefono: "",
        direccion: "",
        dni: "",
        foto: "",
        edad: "",
      },
      eliminarUsuario: {
        id_usuario: "",
      },
    }),
  
    methods: {
      crearUsuarioAPI() {
        axios
          .put("http://127.0.0.1:5050/user", this.crearUsuario, this.config_request)
          .then((response) => {
            console.log("Usuario creado:", response.data);
            this.crearUsuario = {
                nickname: "",
                password: "",
                nombre:"",
                apellido:"",
                genero: "",
                correo_electronico: "",
                telefono: "",
                direccion: "",
                dni: "",
                foto: "",
                edad: "",
            };
          })
          .catch((error) => {
            console.error(error);
          });
      },
  
      eliminarUsuarioAPI() {
        axios
          .delete("http://127.0.0.1:5050/user", { id_usuario: this.eliminarUsuario.id_usuario }, this.config_request)
          .then((response) => {
            console.log("Usuario eliminado:", response.data);
            this.eliminarUsuario.id_usuario = "";
          })
          .catch((error) => {
            console.error(error);
          });
      },
    },
  };
  </script>
  
  <style>
  .fondo3 {
    width: 100%;
    background: url("https://fondosmil.com/fondo/52683.jpg");
  }
  </style>
     
  