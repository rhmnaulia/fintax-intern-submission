<template>
  <v-container class="empContainer mt-5 elevation-2">
    <h1 class="content-title pb-2">Employee List</h1>
    <v-data-table
      :headers="headers"
      :items="list"
      :footer-props="{
        'items-per-page-options': [3, 5, 10, -1],
      }"
      :items-per-page="3"
      class="elevation-3 empTable"
    >
      <template slot="list" slot-scope="props">
        <td>{{ props.employee_name }}</td>
        <td>{{ props.employee_salary }}</td>
        <td>{{ props.employee_age }}</td>
      </template>
    </v-data-table>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'EmployeeList',
  data() {
    return {
      headers: [
        { text: 'Name', value: 'employee_name' },
        { text: 'Sallary', value: 'employee_salary' },
        { text: 'Age', value: 'employee_age' },
        { class: 'dark' },
      ],
      list: [],
    };
  },

  mounted() {
    axios
      .get('http://dummy.restapiexample.com/api/v1/employees')
      .then((res) => {
        this.list = res.data.data;
      })
      .catch(function(error) {
        if (error.response) {
          console.log(error.response.data);
          console.log(error.response.status);
          console.log(error.response.headers);
        }
      });
  },
};
</script>

<style>
.empContainer {
  background: rgb(250, 250, 250);
  border-radius: 5px;
}

tbody tr:nth-of-type(even) {
  background-color: rgb(236, 237, 237);
}

tbody tr:nth-of-type(odd) {
  background-color: rgb(250, 250, 250);
}

.v-data-table-header {
  background-color: #16213e;
  color: white;
}

.v-data-footer {
  background-color: rgb(250, 250, 250);
}

.theme--light.v-data-table thead tr th {
  color: white;
}

th span {
  font-size: 15px;
  color: rgb(250, 250, 250);
}
</style>
