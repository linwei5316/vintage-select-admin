<template>
  <nav aria-label="Page navigation example">
    <ul class="pagination">
      <li class="page-item"
        :class="isDisabled('pre')"
      >
        <a class="page-link" href="#" aria-label="Previous"
          @click.prevent="getData(pagination.current_page - 1)"
        >
          <span aria-hidden="true">&laquo;</span>
          <span class="sr-only">Previous</span>
        </a>
      </li>
      <li class="page-item"
        v-for="page in pagination.total_pages"
        :key="page"
        :class="pageActive(page)"
      >
        <a class="page-link" href="#"
          @click.prevent="getData(page)"
        >
          {{page}}
        </a>
      </li>
      <li class="page-item"
        :class="isDisabled('next')"
      >
        <a class="page-link" href="#" aria-label="Next"
          @click.prevent="getData(pagination.current_page + 1)"
        >
          <span aria-hidden="true">&raquo;</span>
          <span class="sr-only">Next</span>
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
import { mapState, mapActions } from 'vuex'
export default {
  props: {
    module: {
      type: String
    },
    api: {
      type: String
    }
  },
  computed: {
    pagination(){
      return this.$store.state[this.module].pagination
    }
  },
  methods: {
    getData(page){
      this.$store.dispatch(`${this.module}/${this.api}`, page)
    },
    pageActive(page){
      return {
        active: this.pagination.current_page === page
      }
    },
    isDisabled(type){
      return {
        disabled: !this.pagination[`has_${type}`]
      }
    }
  }
}
</script>

<style>

</style>
