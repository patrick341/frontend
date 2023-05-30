<template>
    <div>
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
        <b-form-group
          id="input-group-1"
          label="Nickname:"
          label-for="input-1"
        >
          <b-form-input
            id="input-1"
            v-model="form.nickname"
            placeholder="Ingrese nickname"
            required
          ></b-form-input>
        </b-form-group>
  
        <b-form-group
          id="input-group-2"
          label="Password:"
          label-for="input-2"
        >
          <b-form-input
            id="input-2"
            v-model="form.password"
            type="password"
            placeholder="Ingrese contraseña"
            required
          ></b-form-input>
        </b-form-group>
  
        <b-form-group
          id="input-group-3"
          label="Apellido:"
          label-for="input-3"
        >
          <b-form-input
            id="input-3"
            v-model="form.apellido"
            placeholder="Ingrese apellido"
            required
          ></b-form-input>
        </b-form-group>
  
        <b-form-group
          id="input-group-4"
          label="Nombre:"
          label-for="input-4"
        >
          <b-form-input
            id="input-4"
            v-model="form.nombre"
            placeholder="Ingrese los Nombre Completos"
            required
          ></b-form-input>
        </b-form-group>
  
        <b-form-group
          id="input-group-5"
          label="Edad:"
          label-for="input-5"
        >
          <b-form-input
            id="input-5"
            v-model="form.edad"
            type="number"
            placeholder="Ingrese su edad"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="input-group-6"
          label="dni:"
          label-for="input-6"
        >
          <b-form-input
            id="input-6"
            v-model="form.dni"
            type="text"
            placeholder="Ingrese su documento"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="input-group-7"
          label="genero:"
          label-for="input-7"
        >
          <b-form-input
            id="input-7"
            v-model="form.genero"
            type="text"
            placeholder="Ingrese su genero"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="input-group-8"
          label="Correo Electronico:"
          label-for="input-8"
        >
          <b-form-input
            id="input-8"
            v-model="form.correo_electronico"
            type="text"
            placeholder="Ingrese su correo electronico"
            required
          ></b-form-input>
        </b-form-group>
        
        <b-form-group
          id="input-group-9"
          label="Direccion:"
          label-for="input-9"
        >
          <b-form-input
            id="input-9"
            v-model="form.direccion"
            type="text"
            placeholder="Ingrese su Direccion"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="input-group-10"
          label="Foto:"
          label-for="input-10"
        >
          <b-form-input
            id="input-10"
            v-model="form.foto"
            type="text"
            placeholder="Ingrese la ruta de la foto"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group
          id="input-group-11"
          label="Telefono:"
          label-for="input-11"
        >
          <b-form-input
            id="input-11"
            v-model="form.telefono"
            type="text"
            placeholder="Ingrese su telefono"
            required
          ></b-form-input>
        </b-form-group>

        <b-button type="submit" variant="primary">Crear Usuario</b-button>
        <b-button type="reset" variant="danger">Limpiar</b-button>
      </b-form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';

  export default {
    data() {
      return {
        form: {
          nickname: '',
          password: '',
          apellido: '',
          nombre: '',
          edad: null,
          dni: '',
          genero: '',
          correo_electronico: '',
          direccion:'',
          foto:'',
          telefono:''
        },
        show: true
      };
    },
    methods: {
      onSubmit(event) {
        //event.preventDefault();
        event.preventDefault();
        
        const {
        nickname,
        password,
        apellido,
        nombre,
        edad,
        dni,
        genero,
        correo_electronico,
        direccion,
        foto,
        telefono
        } = this.form;

      const userData = {
        nickname,
        password,
        apellido,
        nombre,
        edad,
        dni,
        genero,
        correo_electronico,
        direccion,
        foto,
        telefono
      };

        
        var config_request={
          headers:{
            'Content-Type': 'application/json',
            'Access-Control-Allow-Origin': '*'
          }
        }
        //const{nickname, password,apellido,nombre,edad,dni,genero,correo_electronico,direccion,foto,telefono} =this.userData
        
        //insertar2(nickname,password,apellido,nombre,edad,dni,genero,correo_electronico,direccion,foto,telefono)
        axios.post('http://127.0.0.1:5050/usuario', this.form, config_request)
          .then(response => {
            // Manejar la respuesta exitosa
            console.log('Usuario creado:', response.data);
            // Limpiar el formulario después de crear el usuario
            this.form = {
              nickname: '',
              password: '',
              apellido: '',
              nombre: '',
              edad: null,
              dni: '',
              genero: '',
              correo_electronico: '',
              direccion:'',
              foto:'',
              telefono:''
            };
          })
          .catch(error => {
            // Manejar el error
            console.error(error);
          });
      
        },
      onReset(event) {
        event.preventDefault();
        // Resetear los valores del formulario
        this.form.nickname = '';
        this.form.password = '';
        this.form.apellido = '';
        this.form.nombre = '';
        this.form.edad = null;
        this.form.dni = '',
        this.form.genero = '',
        this.form.correo_electronico = '';
        this.form.direccion = '';
        this.form.foto ='';
        this.form.telefono ='';
        // Truco para restablecer/borrar el estado de validación del formulario nativo del navegador
        this.show = false;
        this.$nextTick(() => {
          this.show = true;
        });
      }
    }
  };
  </script>
  