<template>
    <div id="app">
      <input type="text" placeholder="Titolo Film o SerieTv:" v-model="searchText">
      <button @click="$emit('searchText', searchText)">Cerca</button>
    </div>
  </template>
  
  <script>

  export default {
    name: 'MyHeader',
    data() {
      return {
        searchText: '',
      }
    },
    
  }
  </script>
  
  <style lang="scss">
  
  </style>
  