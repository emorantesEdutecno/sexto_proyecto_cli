<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!--
<HelloWorld msg="Welcome to Your Vue.js App"/>
  -->
  
  <EventModifierStop />
  <hr>
  <EventModifierCapture />
  <hr>
  <EventModifierSelf />
  <hr>
  <ComponentePadre />



</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import EventModifierStop from '@/components/EventModifierStop.vue';
import EventModifierCapture from '@/components/EventModifierCapture.vue';
import EventModifierSelf from '@/components/EventModifierSelf.vue';
import ComponentePadre from '@/components/ComponentePadre.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    EventModifierStop,
    EventModifierCapture,
    EventModifierSelf,
    ComponentePadre
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
