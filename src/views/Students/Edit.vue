<template>
  <div class="alert" v-if="errors.length > 0">
    <span v-for="error in errors" :key="error">
      {{ error }},
    </span>
  </div>


  <div class="container py-4 my-3">
    <div class="card">
      <div class="card-header">
        <h4>Edit Students</h4>
      </div>
      <div class="card-body">
        <form action="">
          <div class="mb-3 form-group">
            <label for="">Name</label>
            <input type="text" v-model="model.student.name" class="form-control" required>
          </div>
          <div class="mb-3">
            <label for="">Course</label>
            <input type="text" v-model="model.student.course" class="form-control" required>
          </div>
          <div class="mb-3">
            <label for="">Email</label>
            <input type="text" v-model="model.student.email" class="form-control" required>
          </div>
          <div class="mb-3">
            <label for="">Phone</label>
            <input type="text" v-model="model.student.phone" class="form-control" id="validationCustom05" required>
          </div>
          <div class="mb-3">
            <button type="button" @click="updateStudent" class="btn btn-primary">Update</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>


<script>

import axios from 'axios';

export default {


  name: 'studentEdit',
  data() {
    return {
      studentId: "",
      model: {
        student: {
          name: '',
          course: '',
          email: '',
          phone: ''

        }
      },
      errors: [],
      name: '',
      email: '',
      comment: '',
      nameError: false,
      emailError: false,
      commentError: false,
      errors: []
    }
  },
  mounted() {
    console.log(this.$route.params.id)
    this.studentId = this.$route.params.id
    this.getStudentData(this.$route.params.id)

  },
  methods: {

    getStudentData(studentId) {
      axios.get(`http://localhost:3000/students/${studentId}`)
        .then(res => {
          console.log(res.data)
          this.model.student = res.data;
        }).catch(function (error) {
          if (error) {
            alert('Student you tring to edit not found')
          }
        })

    },


    updateStudent() {
      axios.put(`http://localhost:3000/students/${this.studentId}`, this.model.student)
        .then(res => {
          console.log(res.data);
          alert('Student updated succefully')



        })
    },




  }
}

</script>
