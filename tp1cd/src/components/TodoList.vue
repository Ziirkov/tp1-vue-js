<template>
  <div class="todo-list">
    <p>{{errorMessage}}</p>
    <div v-for="(todo, index) in todos"
    :key="index"
    >
      <p>{{todo.person}} doit {{todo.name}} en {{todo.time}} heures. || Status: {{todo.status}}</p>
    div>
  </div>
</template>

