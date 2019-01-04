<template>
  <div>
    <h3>hello</h3>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      unsplashData: [],
      userInput: null,
      clientId: '5f39d0a9e6755434f948e418ab5ce36ae00b133409a4b988c59a633ddbe594ba'
    }
  },

  created () {
    axios.get('https://api.unsplash.com/photos/?client_id=' + this.clientId).then(response => {
      this.unsplashData = response.data
    })
  },

  methods: {
    search () {
      this.unsplashData = null
      axios.get('https://api.unsplash.com/photos/search/?query=' + this.userInput + '&client_id=' + this.clientId).then(response => {
        console.log(response.data)
        this.unsplashData = response.data
      })
    }
  }
}
</script>

<style lang="sass">
@import '../styles/app.sass'


</style>
