<template>
  <div class="container">
    <Header></Header>
    <div class="row my-4">
      <div class="col-12">
        <div class="card">
          <div class="card-header text-center">
            Funcionarios de El Salvador
          </div>
          <div class="card-body">
            <table class="table">
              <thead>
              <tr>
                <th>ID</th>
                <th>Nombre</th>
                <th>Direccion</th>
                <th>Posicion</th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(todo, index) in todos" :key="index">
                <td>{{ todo.id }}</td>
                <td>{{ todo.name }}</td>
                <td>{{ todo.address }}</td>
                <td>{{ todo.position }}</td>
              </tr>
              <infinite-loading @infinite="getTodos"></infinite-loading>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//librerias externas
import axios from 'axios'
//controla el efecto que carga los datos de una tabla, mientras se esta bajando
import InfiniteLoading from 'vue-infinite-loading';

//componentes internos
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header,
    InfiniteLoading
  },
  data() {
    return {
      page: 1,
      todos: []
    }
  },
  methods: {
    getTodos($state) {
      axios
          .get('http://localhost:8080/api/v1/officials.json?page=1=' + this.page)
          .then(response => {
            if (response.data.length) {
              this.page += 1
              this.todos.push(...response.data)
              $state.loaded()
            } else {
              $state.complete();
            }
          })

    }
  }
}
</script>
<style>
</style>
