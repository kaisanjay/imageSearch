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
export default {
  name: 'serchResults',
  data() {
    return {
    };
  },
  methods: {},
  components: {},
};
</script>
