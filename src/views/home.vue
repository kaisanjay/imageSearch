<template>
  <div>
    <homeIcon></homeIcon>
    <div class="hero">
      <searchInput></searchInput>
    </div>
    <!-- pi = pretty image -->
    <div class="pi-tabs">
      <button class="pi-tabs__btn" id="popular-Btn" @click="showTab">Popular</button>
      <button class="pi-tabs__btn" id="saBtn" @click="showTab">Nature</button>
      <button class="pi-tabs__btn" id="saBtn" @click="showTab">Weather</button>
      <button class="pi-tabs__btn" id="saBtn" @click="showTab">Animals</button>
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
    +bp($break-580)
      font-size: 1em
    &:hover
      border-bottom: 2px solid #cccccc
.pi-tabs__active
  font-weight: 900
  color: #7F44D3
  border-bottom: 2px solid #7F44D3
  &:hover
    border-bottom: 2px solid #7F44D3

</style>

<script>
import homeIcon from '@/components/homeIcon.vue'
import searchInput from '@/components/searchInput.vue'
import searchResults from '@/components/searchResults.vue'
import axios from 'axios'
import { bus } from '../main'

export default {
  name: 'home',
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

  mounted () {
    document.querySelector('#popular-Btn').classList.add('pi-tabs__active')
    axios.get('https://api.unsplash.com/photos/search/?query=' + 'popular' + '&client_id=' + this.clientId).then(response => {
      bus.$emit('images', response.data)
    })
  },

  methods: {
    search () {

    },

    showTab (event) {
      let query = event.currentTarget.textContent
      this.unsplashData = null

      document.querySelectorAll('.pi-tabs__btn').forEach((el) => {
          el.classList.remove('pi-tabs__active');
      })

      event.currentTarget.classList.add('pi-tabs__active')

      axios.get('https://api.unsplash.com/photos/search/?query=' + query + '&client_id=' + this.clientId).then(response => {
        // console.log(response.data)
        // this.unsplashData = response.data
        bus.$emit('images', response.data)
      })
      // window.location.href = '/search-page'

    }
  }
}
</script>

