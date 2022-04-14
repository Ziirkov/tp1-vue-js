<template>
    <div class="todos-form">
        <input v-model="todoName" type="text" placeholder="Name of the todo"/>
        <input v-model="todoTime" type="number" :min="0" :max="10" placeholder="Temps d'estimation"/>
        <select v-model="todoPerson" >
            <option disabled value="">Responsable</option>
            <option>John</option>
            <option>Doe</option>
            <option>Foo</option>
        </select>
        <input type="submit" value="Bouton" @click="addTodo()" />
    </div>
</template>

<script>
export default {
  name: 'TodosForm',

  props:{},
  data: () => ({
      errorMessage: '',
      todoName: '',
      todoTime: '',
      todoPerson: '',
      todos: []
  }),
  methods: {
    addTodo() {
      if(this.todoName.length === 0 || this.todoTime.length === 0 || this.todoPerson.length === 0  )
      {
        this.errorMessage = 'Veuillez remplir tous les champs !'
      }else {
          this.todos.push({
            person: this.todoPerson,
            name: this.todoName,
            time: this.todoTime,
            status: 'A faire'
        })
        this.errorMessage = ''
      }
    },
  },
}
</script>