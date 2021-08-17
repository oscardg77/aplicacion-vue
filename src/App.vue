<template>
  <div>
    <div id="header">
    <Search v-on:query-change="querySearch" />
    </div>
    <div id="main-container">
    <h2>Todos</h2>
    <TodosAdd v-on:add-todo="addTodo" />
    <Todos v-bind:todosList="copyTodos" v-on:delete-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import Search from './components/Search';
import Todos from './components/Todos';
import TodosAdd from './components/TodosAdd';

export default {
  name: 'App',
  components: {
     Search,
     Todos,
     TodosAdd
    
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id );
      this.copyTodos = [... this.todos];
    },
      addTodo(){
        this.todos.push();
        this.copyTodos = [... this.todos];
      },
      querySearch(query){
        if(query.trim() === ''){
           this.copyTodos = [... this.todos];
        }else{
          const temp = this.todos.filter(todo => {
           return todo.title.includes(query)
          });

          this.copyTodos = [...temp];
        }
      }

  },
  data(){ 
    return {
      todos: [
        {
          id: 0,
          title: 'comprar la cena',
          completed: false
        },
           {
          id: 1,
          title: 'fregar los platos',
          completed: true
        },
           {
          id: 2,
          title: 'ver la television',
          completed: false
        },
         {
           id: 3,
           title: 'terminar tutorial',
           completed: true
         }
      ],
      copyTodos: []
    }
  },
  created() {   
   this.copyTodos = [... this.todos];
}
  }
</script>

<style>
/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
* {
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5em;
  padding: 0;
  margin: 0;
}
#main-container {
  border: solid 1px #ccc;
  width: 600px;
  margin: 100px auto;
}
#header {
  background: #ccc;
}
h2 {
  padding: 0 10px;
}
</style>
