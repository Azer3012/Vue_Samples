<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h4>
          students
          <RouterLink class="btn btn-primary float-end" to="/student/create"
            >add student</RouterLink
          >
        </h4>
      </div>
      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>ID</th>
              <th>name</th>
              <th>username</th>
              <th>email</th>
              <th>Action</th>
            </tr>
          </thead>
          <tbody v-if="this.students.length>0">
            <tr v-for="student in this.students" :key="student.id">
              <td>{{ student.id }}</td>
              <td>{{ student.name }}</td>
              <td>{{ student.username }}</td>
              <td>{{ student.email }}</td>
              <td>
                <RouterLink class="btn btn-success" to="/"
                  >Edit student</RouterLink
                >

                <button type="button" class="btn btn-danger">Delete</button>
              </td>
            </tr>
          </tbody>
          <tbody v-else>
            <tr>
                <td colspan="5">Loading...</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "students",
  data() {
    return {
      students: [],
    };
  },
  mounted() {
    this.getStudents();
  },
  methods: {
    getStudents() {
      axios.get("https://jsonplaceholder.typicode.com/users").then((res) => {
        this.students = res.data;
      });
    },
  },
};
</script>
