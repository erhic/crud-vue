<template>
  <div class="container py-4">
    <div class="card">
      <div class="card-header">
        <h4>
          Students
          <RouterLink to="/student/create" class="btn btn-primary float-end">Add Students</RouterLink>
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
          <tbody>
            <tr>

            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: 'students',
  data() {
    return {
      students: []
    }
  },
  mounted() {
    console.log('i am')
  }
}


</script>

<style></style>
