<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>


    <div class="wrapper">
      <nav class="navbar navbar-expand-xl navbar-info bg-info">
        <div class="container-fluid">
          <RouterLink class="navbar-brand" to="/">Customer Manager</RouterLink>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarWithDropdown"
            aria-controls="navbarWithDropdown" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse show" id="navbarWithDropdown">
            <ul class="navbar-nav ms-auto">
              <li class="nav-item">
                <RouterLink class="nav-link active" aria-current="page" to="/">Home</RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" to="/about">About Us</RouterLink>
              </li>
              <li class="nav-item">
                <RouterLink class="nav-link" to="/customers">Customer</RouterLink>
              </li>

            </ul>
          </div>
        </div>
      </nav>
    </div>
  </header>
  <View />
  <RouterView />
</template>

<style scoped></style>
