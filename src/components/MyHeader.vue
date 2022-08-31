<template>
    <div id="app">
      <header>
        <h2>BOOLFLIX</h2>
        <input @keyup="$emit('searchText', searchText)" type="text" placeholder="Titolo Film o SerieTv:" v-model="searchText">
      </header>
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
  
  <style scoped lang="scss">
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 80px;
      padding: 0 25px;
      background-color: black;
      h2 {
        color: red;
        font-size: 45px;
      }
      input {
        padding: 5px;
        font-weight: 700;
      }
    }
  </style>
  