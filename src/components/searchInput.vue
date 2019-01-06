<template>
  <div>
    <div class="newsletter">
      <input type="text"
      v-model="userInput"
      id="emailInput"
      @keyup.enter="search"
      placeholder="Search photos">
      <button @click="search">
        Sign Up
      </button>
    </div>
  </div>
</template>

<style lang="sass">
@import '../styles/app.sass'

</style>

<script>
export default {
  name: 'searchInput',
  data() {
    return {
    };
  },
  methods: {
    search () {}
  },
  components: {},
};
</script>
