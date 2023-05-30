<template>
    <div>
      <ul>
        <li v-for="user in users" :key="user.id_usuario">
          {{ user.nickname }} - {{ user.name }}
          <button @click="editUser(user)">Editar</button>
        </li>
      </ul>
  
      <div v-if="selectedUser">
        <h3>Editar Usuario</h3>
        <form @submit="updateUser">
          <label>Nickname:</label>
          <input type="text" v-model="selectedUser.nickname" required>
          <br>
          <label>Nombre:</label>
          <input type="text" v-model="selectedUser.name" required>
          <br>
          <button type="submit">Actualizar</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        users: [],
        selectedUser: null
      };
    },
    methods: {
      editUser(user) {
        this.selectedUser = { ...user };
      },
      updateUser(event) {
        event.preventDefault();
  
        var config = {
          headers: {
            'Content-Type': 'application/json',
            'Access-Control-Allow-Origin': '*'
          }
        };
  
        axios
          .patch('http://127.0.0.1:5050/user', this.selectedUser, config)
          .then(response => {
            console.log('Usuario actualizado:', response.data);
            this.selectedUser = null; // Limpiar el usuario seleccionado
            this.fetchUsers(); // Actualizar la lista de usuarios después de la actualización
          })
          .catch(error => {
            console.error(error);
          });
      },
      fetchUsers() {
        axios
          .patch('http://127.0.0.1:5050/user')
          .then(response => {
            this.users = response.data;
          })
          .catch(error => {
            console.error(error);
          });
      }
    },
    created() {
      this.fetchUsers();
    }
  };
  </script>