<template>
  <button @click="test">test</button>
</template>
<script>
import importHTML from 'import-html-entry'
export default {
  name: 'App',
  data() {
    return {
      x: '1',
    }
  },
  methods: {
    test() {
      importHTML('demo.html').then((res) => {
        debugger
        console.log(res.template)

        res.execScripts().then((exports) => {
          const mobx = exports
          const { observable } = mobx
          observable({
            name: 'kuitos',
          })
        })
      })
    },
  },
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
