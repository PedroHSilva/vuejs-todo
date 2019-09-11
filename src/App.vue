<template>
  <div id="app">
    <h1>Lista de Tarefas</h1>
    
    <ul>
        <input type="text" placeholder="enter item" v-on:keyup.enter="addTodo()" v-model="text">
        <li v-for="item in list" @click="checkItem(item)" v-bind:class="[item.checked ? 'completed' : '']"> 
          <input class="checked-item" type="checkbox" v-bind:checked=item.checked >
          <span> {{ item.text }} </span>
          <button v-on:click="removeTodo(item)">X</button> 
        </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      completed_item: '',
      checked: false,
      show: true,
      text:'',
      list: [
        { "text": "Adicionar mais itens a sua lista", checked: true},
      ]
    }
  },

  methods: {
    addTodo() {
      if(this.text.trim() !== '') {
        this.list.push({ text: this.text, checked: false });
        this.text = '';
      }
    },

    removeTodo(item) {
      this.list.splice(this.list.indexOf(item), 1);
    },

    checkItem(item) {
      if(this.list[this.list.indexOf(item)]) {
        this.list[this.list.indexOf(item)].checked ? this.list[this.list.indexOf(item)].checked = false : this.list[this.list.indexOf(item)].checked = true;
      }
    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  text-align: ;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
  width: 100%;
}

li {
  display: inline-block;
  background: #353535;
  color: #fff;
  border-bottom: 01px solid rgb(255, 255, 255);
  padding: 10px;
  width: 100%;
}

li.completed {
  background: #c7c7c7;
  color: rgb(150, 150, 150);
  border-bottom: 01px solid #338f66;
  text-decoration: line-through;
}

a {
  color: #42b983;
}
input {
  padding: 10px;
  width: 100%; 
  margin-bottom: 05px;
}

.checked-item {
  float: left;
  width: 10px;
  margin: 7px 10px 0 0;
}

button {
  float: right;
}

</style>
