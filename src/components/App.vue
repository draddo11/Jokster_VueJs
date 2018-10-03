<template>
    <div id ='app'>
       <h3>Got Jokes</h3>
       <button class='btn btn-primary ' id='btn1'  @click='initJokes'>Add Ten Random Jokes</button>
        ||
       <button class='btn btn-primary' @click='addJoke'> Add A Joke </button>
       <br>
      <span v-for='type in types'>
        <input 
        type='checkbox' 
        :value='type' 
        v-model='checkedTypes'
        checked>
        <label>{{type}}</label>&nbsp;
      </span>
       <br>
       <br>
       <div class ='col-md-12'>
         <joke
         v-for='(joke,index) in $store.state.jokes'
         v-show='checkedTypes.includes(joke.type)'
         :joke='joke'
         :index='index'
         key="index"
         />
    </div>
    </div>
</template>

<script>
import {mapActions} from 'vuex'
import Joke from './Joke.vue'
export default {
  data(){
    return {
      types:['general', 'knock-knock', 'programming'],
      checkedTypes:['general','knock-knock', 'programming']
    }
  },
  methods: mapActions([
    'initJokes',
    'addJoke'
  ]),
  components:{
    Joke
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color:antiquewhite; */
  /* background-color:#2c3e50; */
  margin-top:60px;
}
body{
  /* background-color:#2c3e50; */
}

.joke-card{
  border:2px solid #4fc08d;
  border-radius: 2px;
  padding:5px;
  margin: 5px;
  cursor:pointer;

}

.btn1{
margin :5px;
padding-right: 10px;
}
</style>
