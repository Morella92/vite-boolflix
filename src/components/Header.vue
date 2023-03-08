<template>
   <div class="flex-container">
        <h1 class="header-logo">boolflix</h1>
        <div class="search-bar">
            <input class="header-input" type="text" v-model="userSearch" @keyup.enter="searchClicked" placeholder="Cerca il film o la serie tv">
            <button class="header-button" @click="searchClicked"> Cerca </button>
        </div>
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
    .flex-container{
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-top: 15px;
    }
    .header-logo{
        color: red;
        text-transform: uppercase;
    }

     .header-input{
        
        padding: 10px;
    }

    .header-button{
        padding: 10px 15px;
        margin-left: 20px;
        background-color: rgb(105, 99, 99);
        color: white;
    }
</style>
