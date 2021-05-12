<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/peiko-logo-mini.png">
    <h1>Test</h1>
    <hr>
    
    <TestTask />
  </div>
</template>

<script>
import TestTask from '@/components/Test-task'

export default {
  name: 'App',
  components: {
    TestTask
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
