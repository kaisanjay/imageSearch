<template>
  <div>
    <homeIcon></homeIcon>
    <searchInput></searchInput>
    <searchResults></searchResults>
  </div>
</template>

<style lang="sass">
@import '../styles/app.sass'

</style>

<script>
import axios from 'axios'
import homeIcon from '@/components/homeIcon.vue'
import searchInput from '@/components/searchInput.vue'
import searchResults from '@/components/searchResults.vue'

export default {
  name: 'searchPage',
  components: {
    searchInput,
    searchResults,
    homeIcon
  },
  data () {
    return {
      unsplashData: [],
      userInput: null,
      clientId: '5f39d0a9e6755434f948e418ab5ce36ae00b133409a4b988c59a633ddbe594ba'
    }
  },

  beforeCreate () {
    axios.get('https://api.unsplash.com/photos/?client_id=' + this.clientId).then(response => {
      this.unsplashData = response.data
    })
  },

  methods: {
  }
}
</script>

