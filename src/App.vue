<template>
  <Tabs @tabChange="onChange"></Tabs>
  <show-list-assets v-if="isSwitched" :listData="listData"></show-list-assets>
  <Form v-else @saved="pushData"></Form>
</template>

<script>

  import Tabs from './components/Tabs.vue'
  import ShowListAssets from './components/ShowListAssets.vue'
  import Form from './components/Form.vue'

  export default {
    name: 'App',
    components: {
      Tabs,
      ShowListAssets,
      Form
    },
    data() {
      return {
        isSwitched: true,
        listData: []
      }
    },
    methods: {
      onChange(isSwitched) {
        this.isSwitched = isSwitched
      },
      pushData(data) {
        this.listData.push(data)
      }
    }
  }
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    list-style: none;
    outline: none;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    background-color: rgb(245, 245, 245);

  }

  body #app {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    flex-direction: column;

  }

</style>
