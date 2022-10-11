<template>
  <h1>Chat</h1>
  <div>
    <div v-for="(message, index) in messages" :key="index">
      <p><strong>{{message.data.address}}:{{message.data.port}}</strong> - {{message}}</p>
    </div>
  </div>
</template>

<script>
import { ipcRenderer } from 'electron'

export default {
  name: 'App',
  data: function () {
    return {
      messages: []
    }
  },
  mounted() {
    console.log("mounted")
    ipcRenderer.on('message', (data) => console.log(data))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
