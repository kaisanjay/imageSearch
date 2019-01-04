<template>
  <div>
     <div v-for="a in unsplashData" class="test">
         <img :src="a.urls.small">
     </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      unsplashData: []
    }
  },

  created () {
    const clientId = '5f39d0a9e6755434f948e418ab5ce36ae00b133409a4b988c59a633ddbe594ba'
    axios.get('https://api.unsplash.com/photos/?client_id=' + clientId).then(response => {
      this.unsplashData = response.data
    })
  }
}
</script>

<style lang="sass">

@import '../styles/app.sass'


</style>
