<template>
  <nav class="navbar navbar-dark fixed-top bg-dark flex-md-nowrap p-0 shadow">
    <router-link class="navbar-brand col-sm-3 col-md-2 mr-0" to="/admin/products">Vintage Select Admin</router-link>
    <!-- <input class="form-control form-control-dark w-100" type="text" placeholder="Search" aria-label="Search"> -->
    <ul class="navbar-nav px-3">
      <li class="nav-item text-nowrap">
        <a
          class="nav-link"
          href="#"
          @click.prevent="logOut"
        >
          登出
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  methods: {
    ...mapActions('adminUser', ['logOut'])
  }
}
</script>

<style>

</style>
