<template>
   <div class="search-bar">
        <h1 class="header-logo">boolfix</h1>
        <input class="header-input" type="text" v-model="userSearch" placeholder="Cerca il film o la serie tv">
        <button class="header-button" @click="searchClicked"> Cerca </button>
    </div>
</template>
  
<script>
    export default {
      data() {
        return {
          userSearch: ''
        }
      },
      methods: {
        searchClicked() {
          this.$emit('search', this.userSearch)
        }
      }
    }
</script>
  

<style lang="scss" scoped>
     .header-input{
        margin-top: 50px;
        padding: 10px;
    }

    .header-button{
        padding: 10px 15px;
        margin-left: 20px;
        background-color: black;
        color: white;
    }
</style>
