<template>
  <div>
    <div class="newsletter">
      <input type="text"
      v-model="userInput"
      id="userInputId"
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
import axios from 'axios'
import { bus } from '../main'

export default {
  name: 'searchInput',
  data() {
    return {
      userInput: null,
      clientId: '5f39d0a9e6755434f948e418ab5ce36ae00b133409a4b988c59a633ddbe594ba'
    };
  },
  methods: {
    search (event) {
      this.unsplashData = null

      axios.get('https://api.unsplash.com/photos/search/?query=' + this.userInput + '&client_id=' + this.clientId).then(response => {
        bus.$emit('images', response.data)
        // window.location.href = '/search-page'

        // if (window.location.pathname === '/')

      })
    }
  },
  components: {},
};
</script>
