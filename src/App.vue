<template>
  <div class="app-main">
    <chat-container-component/>
    <MainContainerComponent/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import ChatContainerComponent from "@/components/ChatContainerComponent";
import MainContainerComponent from "@/components/MainContainerComponent";
export default {
  name: 'App',
  components: {
    MainContainerComponent,
    ChatContainerComponent,
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
