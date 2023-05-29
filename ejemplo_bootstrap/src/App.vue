<template>
  <div id="app">
    
    <Componentes23/>
    <CreateUser/>
    <DeleteUser/>
    <UpdateComponent/>
    <!---<TablaComponent/>
      <FrontComponent/>
      <ComponenteMaestro/>
      <HelloWorld/>
      <Tabla2Component/>-->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import TablaComponent from './components/TablaComponent.vue';
import Tabla2Component from './components/Tabla2Component.vue';
import FrontComponent from './components/FrontComponent.vue';
import Componentes23 from './components/Componentes23.vue';
import CreateUser from './components/CreateUser.vue';
import ComponenteMaestro from './components/ComponenteMaestro.vue';
import DeleteUser from './components/deleteUser.vue';
import UpdateComponent from './components/UpdateComponent.vue';


export default {
  name: 'App',
  components: {
    HelloWorld,
    TablaComponent,
    Tabla2Component,
    FrontComponent,
    Componentes23,
    CreateUser,
    ComponenteMaestro,
    DeleteUser,
    UpdateComponent
}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
