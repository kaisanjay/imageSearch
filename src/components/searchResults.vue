<template>
  <div>
    <div class="container">
      <div v-for="a in unsplashData" class="image-card">
        <img :src="a.urls.small">
        <div class="image-card--content">
          <h4><b>Photographer:&nbsp;&nbsp;{{ a.user.first_name }}</b></h4>
          <p><b>Total likes:</b>&nbsp;&nbsp;{{ a.user.total_likes }}</p>
          <p><b>Location:</b>&nbsp;&nbsp;{{ a.user.location }}</p>
        </div>
      </div>
      <div v-if="unsplashData.length === 0">
        <h4 style="text-align: center;"><b>No Results Found</b></h4>
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
      gthis.unsplashData = data
    })
  },
  methods: {},
  components: {},
};
</script>
