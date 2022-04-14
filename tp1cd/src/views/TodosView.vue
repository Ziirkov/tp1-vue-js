<template>
    <div class="todos">
        <h1>Ma liste de Todos</h1>
        <TodosForm />
    </div>
</template>

<script>

import TodosForm from '@/components/TodosForm.vue';

export default {
  name: 'HomeView',
  components: {
    TodosForm,
  },
};

</script>