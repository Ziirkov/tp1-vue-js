<template>
  <div class="todos-form">
    <input v-model="todoName" type="text" placeholder="Name of the todo" />
    <input
      v-model="todoTime"
      type="number"
      :min="0"
      :max="10"
      placeholder="Temps d'estimation"
    />
    <select v-model="todoPerson">
      <option disabled value="">Responsable</option>
      <option>John</option>
      <option>Doe</option>
      <option>Foo</option>
    </select>
    <input type="submit" value="Bouton" @click="addTodo()" />

    <div class="todo-list">
      <p>{{ errorMessage }}</p>
      <table class="todo-list-table">
        <tr>
          <th>Personne</th>
          <th>Todo</th>
          <th>Temps</th>
        </tr>
        <tr v-for="(todo, index) in todos" :key="index">
          <td>{{ todo.person }}</td>
          <td>{{ todo.name }}</td>
          <td>{{ todo.time }}</td>
          <td
            class="status-text"
            @click="changeStatus(index)"
            :class="{
              'status-text-todo': todo.status === 'A faire',
              'status-text-ongoing': todo.status === 'En cours',
              'status-text-finished': todo.status === 'Terminé',
            }"
          >
            {{ todo.status }}
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodosForm",
  data: () => ({
    errorMessage: "",
    todoName: "",
    todoTime: "",
    todoPerson: "",
    todos: [],
    statuses: ["A faire", "En cours", "Terminé"],
  }),
  methods: {
    addTodo() {
      if (
        this.todoName.length === 0 ||
        this.todoTime.length === 0 ||
        this.todoPerson.length === 0
      ) {
        this.errorMessage = "Veuillez remplir tous les champs !";
      } else {
        this.todos.push({
          person: this.todoPerson,
          name: this.todoName,
          time: this.todoTime,
          status: "A faire",
        });
        this.errorMessage = "";
      }
    },
  },
  changeStatus(index) {
    let statusIndex = this.statuses.indexOf(this.todos[index].status);

    if (++statusIndex > 2) statusIndex = 0;
    this.todos[index].status = this.statuses[statusIndex];
  },
};
</script>

<style>
.todo-list {
  display: flex;
  justify-content: center;
  border: 1px solid black;
}

.status-text {
  font-weight: bold;
  cursor: pointer;
}
</style>