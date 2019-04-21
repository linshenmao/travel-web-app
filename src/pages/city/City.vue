<template>
  <div>
    <Header></Header>
    <Search :cities='cities'></Search>
    <List :hotCities='hotCities' :cities='cities' :letter='letter'></List>
    <Alphabet
    :cities='cities'
    @change="handleLetterClick"></Alphabet>
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header'
import Search from './components/Search'
import List from './components/List'
import Alphabet from './components/Alphabet'
export default {
  name: 'City',
  components: {
    Header,
    Search,
    List,
    Alphabet
  },
  data () {
    return {
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.getCityInfoSucc)
    },
    getCityInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.hotCities = data.hotCities
        this.cities = data.cities
      }
    },
    handleLetterClick (letter) {
      this.letter = letter
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>

<style lang='stylus' scoped>

</style>
