<template>
  <div id="app">
    <CitasMedicas />
  </div>
</template>

<script>
import CitasMedicas from './components/CitasMedicas.vue';

export default {
  name: 'App',
  components: {
    CitasMedicas,
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>

