<template>
    <div>
      <ul>
        <li v-for="user in users" :key="user.id_usuario">
          {{ user.nickname }} - {{ user.name }}
          <button @click="deleteUser(user.id_usuario)">Eliminar</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        users: []
      };
    },
    methods: {
      deleteUser(userId) {
        var config = {
          headers: {
            'Content-Type': 'application/json',
            'Access-Control-Allow-Origin': '*'
          }
        };
  
        axios
          .delete('http://127.0.0.1:5050/user/${userId}', config)
          .then(response => {
            console.log('Usuario eliminado:', response.data);
            // Actualizar la lista de usuarios después de eliminar uno
            this.fetchUsers();
            
        })
          .catch(error => {
            console.error(error);
          });
      },
      fetchUsers() {
        axios
          .post('http://127.0.0.1:5050/users')
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
  