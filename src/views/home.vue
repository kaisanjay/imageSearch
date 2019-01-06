<template>
  <div>
    <div class="landingPage--title shinyBtn" onclick="window.location='/'">
      <h1>Pre<span style="color: grey;">TT</span>y<span style="font-weight: 400; color: grey;">images</span></h1>
    </div>
    <div class="landingPage__hero">
      <searchInput></searchInput>
    </div>
    <div class="pi-tabs">
      <button class="pi-tabs__btn" id="tpBtn" @click="showTab">Popular</button>
      <buttton class="pi-tabs__btn" id="saBtn" @click="showTab">Nature</buttton>
      <buttton class="pi-tabs__btn" id="saBtn" @click="showTab">Weather</buttton>
      <buttton class="pi-tabs__btn" id="saBtn" @click="showTab">Animals</buttton>
    </div>

    <searchResults></searchResults>
  </div>
</template>

<style lang="sass">
@import '../styles/app.sass'

.pi-tabs
  display: flex
  justify-content: center
  margin-bottom: 4%
  &__btn
    display: block
    font-size: 1.3em
    cursor: pointer
    padding: 12px 16px
    font-weight: bold
    outline: 0
    border: none
    border-bottom: 2px solid transparent
    background-color: transparent
    &:hover
      border-bottom: 2px solid #cccccc
.vw-tabs__active
  font-weight: 900
  color: #7F44D3
  border-bottom: 2px solid #7F44D3
  &:hover
    border-bottom: 2px solid #7F44D3

</style>

<script>
import searchInput from '@/components/searchInput.vue'
import searchResults from '@/components/searchResults.vue'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    searchInput,
    searchResults
  },
  data () {
    return {
      unsplashData: [],
      userInput: null,
      clientId: '5f39d0a9e6755434f948e418ab5ce36ae00b133409a4b988c59a633ddbe594ba'
    }
  },

  created () {
  },

  methods: {
    search () {

    },

    showTab (event) {
      // let query = event.currentTarget.textContent
      // this.unsplashData = null
      // axios.get('https://api.unsplash.com/photos/search/?query=' + query + '&client_id=' + this.clientId).then(response => {
      //   this.unsplashData = response.data
      // })
      window.location.href = '/search-page'

    }
  }
}
</script>

