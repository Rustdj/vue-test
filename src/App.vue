<template>
  <div class="container">
    <AddRecipe :onAdd="addRecipe"/>
    <hr>
    
    <div>
      <RecipeList @select="selectRecipe" :recipes="recipes" />
      <RecipeDetail :recipe="current" @remove="removeRecipe" />
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import AddRecipe from './components/AddRecipe.vue'
import RecipeDetail from './components/RecipeDetail.vue'
import RecipeList from './components/RecipeList.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    AddRecipe,
    RecipeList,
    RecipeDetail
  },
  data() {
    return {
      recipes: [],
      current: null
    }
  },
  methods: {
    addRecipe(recipe) {
      this.recipes.push(recipe)
      
    },
    selectRecipe(id) {
      this.current = this.recipes.find(r => r.id === id)
    },
    removeRecipe(id) {
      this.current = null
      this.recipes = this.recipes.filter(r => r.id !== id)
    }
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
  @import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
  * {
    margin: 0;
    padding: 0;
  }
  body {
    font-family: 'Roboto', sans-serif;
    color: #222;
  }
  a {
    text-decoration: none;
    color: darkblue;
    transition: .3s all ease;
  }
  .center {
    text-align: center;
  }
  a:hover {
    cursor: pointer;
    opacity: .7;
    text-decoration: underline;
  }
  .container {
    max-width: 1000px;
    margin: 0 auto;
    height: 100vh;
  }
  .columns {
    display: flex;
  }
  .detail, .list {
    width: 50%;
    border: 1px solid #eee;
  }
  .list {
    border-right: 0;
  }
  .btn {
    border-radius: 5px;
    background: darkblue;
    color: #fff;
    padding: 6px 14px;
    cursor: pointer;
  }
  .btn:disabled {
    background-color: #eee;
    color: black;
    cursor: not-allowed;
  }
  .btn.remove {
    background: darkred;
  }
  .btn.secondary{
    background: grey;
  }
</style>
