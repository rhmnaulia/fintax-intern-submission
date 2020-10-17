<template>
  <v-container>
    <EmployeeList />
    <Todos />
  </v-container>
</template>

<script>
import EmployeeList from '../components/EmployeeTable/EmployeeList';
import Todos from '../components/Todolist/Todos';
export default {
  name: 'Home',

  components: { Todos, EmployeeList },
};
</script>
