<script>
import axios from "axios"
export default {
  name: 'students',
  data() {
    return {
      students: []
    }
  },
  mounted() {
    // console.log('i am ............')
    this.getStudents();
  },
  methods: {
    getStudents() {
      axios.get('http://localhost:3000/students').then(res => {
        this.students = res.data
        console.log(res)
      });
    }
  }
}


</script>


<template>
  <div class="container py-4">
    <div class="card">
      <div class="card-header">
        <h4>
          Students
          <RouterLink to="/students/create" class="btn btn-primary float-end">Add Students</RouterLink>
        </h4>
      </div>
      <div class="card-body">
        <table class="table">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Course</th>
              <th>Email</th>
              <th>Phone</th>
              <th>Created At</th>
              <th>Action</th>
            </tr>
          </thead>
          <tbody v-if="this.students.length > 0">
            <tr v-for="(student, index) in this.students" :key="index">
              <td>{{ student.id }}</td>
              <td>{{ student.name }}</td>
              <td>{{ student.course }}</td>
              <td>{{ student.email }}</td>
              <td>{{ student.phone }}</td>
              <td>{{ student.created }}</td>
              <td>
                <RouterLink :to="{ path: '/students/' + student.id + '/edit' }" class="btn btn-success px-4 mx-3">
                  Edit
                </RouterLink>
                <button type="button" class="btn btn-danger"> Delete </button>
              </td>

            </tr>
          </tbody>
          <tbody v-else>
            <td colspan="8">
              <p class="text-center m-5 p-5">Loading.....</p>
            </td>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>




<style></style>
