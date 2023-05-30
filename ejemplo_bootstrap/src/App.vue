<template>
  <div id="app">
    <CreateUserComponenteFinal/>
    <UltimoComponenteUpdate/>
    <ComponenteEliminar/>
    <UpdateFinalUsuario/>
    <Create/>
    <Update/>
    <Delete/> 
    <!---
      <Componentes23/>
      <CreateUser/>
      <DeleteUser/>
      <UpdateComponent/>
      <TablaComponent/>
      <FrontComponent/>
      <ComponenteMaestro/>
      <HelloWorld/>
      <CreateFinal/>
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
import CreateUserComponenteFinal from './components/CreateUserComponenteFinal.vue';
import CreateFinal from './components/CreateFinal.vue';
import UpdateFinalUsuario from './components/UpdateFinalUsuario.vue';
import UltimoComponenteUpdate from './components/UltimoComponenteUpdate.vue';
import ComponenteEliminar from './components/ComponenteEliminar.vue';
import Create from './components/Create.vue';
import Update from './components/Update.vue';
import Delete from './components/Delete.vue';

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
    UpdateComponent,
    CreateUserComponenteFinal,
    CreateFinal,
    UpdateFinalUsuario,
    UltimoComponenteUpdate,
    ComponenteEliminar,
    Create,
    Update,
    Delete,
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
