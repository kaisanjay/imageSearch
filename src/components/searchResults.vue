<template>
  <div>
    <div class="row">
      <div v-for="a in unsplashData">
        <img :src="a.urls.regular" style="width: 40%;">
      </div>
    </div>
  </div>
</template>

<style lang="sass">
@import '../styles/app.sass'

</style>

<script>
import { bus } from '../main'

export default {
  name: 'serchResults',
  data() {
    return {
        unsplashData: null
    };
  },

  created () {
    let gthis = this
    bus.$on('images', (data) => {
      console.log(data, 'sanjay')
      gthis.unsplashData = data
    })
  },
  methods: {},
  components: {},
};
</script>
