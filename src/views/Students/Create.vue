<template>
  <div class="alert" v-if="errors.length > 0">
    <span v-for="error in errors" :key="error">
      {{ error }},
    </span>
  </div>


  <div class="container py-4 my-3">
    <div class="card">
      <div class="card-header">
        <h4>Add Students</h4>
      </div>
      <div class="card-body">
        <div class="mb-3">
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
          <button type="button" @click="saveStudent" class="btn btn-primary">Save</button>
        </div>
      </div>
    </div>
  </div>
</template>


<script>

import axios from 'axios';

export default {


  name: 'studentCreate',
  data() {
    return {
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
  methods: {
    saveStudent() {
      axios.post('http://localhost:3000/students', this.model.student).then(res => {
        console.log(res.data);
        this.model.student = {
          name: '',
          course: '',
          email: '',
          phone: ''

        }

      }).catch((errors) => {
        if (!this.firstName) {
          this.errors.push('First name required');
        }
        if (!this.lastName) {
          this.errors.push('Last name required');
        }
        if (!this.email) {
          this.errors.push('Email required');
        }
      })

    },
    validate() {
      this.errors = [];
      var len = this.name.length;
      if (len < 5 || len > 20) {
        this.nameError = true;
        this.errors.push({
          'message': 'Name must be between 5 to 20 characters long.'
        });
      } else {
        document.getElementById('name').className = "form-control is-valid";
        this.errors.push({
          'message': 'Validated.'
        });
        document.getElementById('feedback-1').className = "valid-feedback";
      }
      // email validate
      if (this.email.length < 10 || this.email.search('@') == -1) {
        this.emailError = true;
        this.errors.push({
          'message': 'Please provide a valid email address.'
        });
      } else {
        document.getElementById('email').className = "form-control is-valid";
        this.errors.push({
          'message': 'Validated.'
        });
        document.getElementById('feedback-2').className = "valid-feedback";
      }
      // comment validate
      var regex = /^[a-zA-Z0-9 .-]+$/;
      if (this.comment.length < 20 || this.comment.match(regex) == null) {
        this.commentError = true;
        this.errors.push({
          'field': 'comment',
          'message': 'Comment must be of 20 characters or more and use of special characters except . and - are restricted'
        });
      } else {
        document.getElementById('comment').className = "form-control is-valid";
        this.errors.push({
          'message': 'Validated.'
        });
        document.getElementById('feedback-3').className = "valid-feedback";
      }
    }
  }
}

</script>