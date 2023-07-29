<template>
  <div class="about">
    <p v-for="stud in customers" :key="stud.id">{{ customers.email }}</p>
    <customers />
  </div>
</template>
<script>
import customers from '@/views/Customers/View.vue'
export default {

  name: 'AboutView',
  components: {
    customers
  },
  props: {
    name: String,
    data: Object,
    getCustomers: Function
  }
}
</script>

<style></style>
