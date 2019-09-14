<template>
  <div id="app">
    <h1>Lista de Tarefas</h1>
    <ul class="w3-ul w3-card-2">
        <input type="text" class="w3-input" placeholder="enter item" v-on:keyup.enter="addTodo()" v-model="text">
        <li v-for="item in list" v-bind:class="[item.checked ? 'w3-grey' : ''] + ' w3-bar'"> 
          <i class="w3-bar-item w3-xlarge fa fa-check-circle"></i>
          <input class="w3-hide" type="checkbox" v-bind:checked=item.checked >
          <span class="w3-bar-item" @click="checkItem(item)"> {{ item.text }} </span>
          <i class="w3-bar-item w3-xlarge w3-right fa fa-times-circle" v-on:click="removeTodo(item)"></i> 
        </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      checked: false,
      show: true,
      text:'',
      list: []
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
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  margin-top: 60px;
} 

</style>
