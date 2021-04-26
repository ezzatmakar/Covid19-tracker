<template>
  <main v-if="!loading">
    <Data-title :text="title" :dataDate="dataDate" />
  </main>
  <main class="flex flex-col align-center justify-center text-center mb-4" v-else>
    <div class="text-ger-500 text-3xl mt-10 mb-6">
      Fetching Data 
    </div>
    <img :src="loadingImage" class="m-auto" />
  </main>
  <Data-Boxes :stats="stats" />

  <CountrySelect @get-country="getCountryData" :countries="countries" />
  <div v-if="stats.Country" class="text-center pt-3">
    <button
        @click="clearCountryData"
        class="shadow-md bg-blue-100 text-blue-700 hover:text-red-600 py-2 px-4 border border-blue-500 rounded">
      Clear selected
    </button>
  </div>

</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
    DataTitle, 
    DataBoxes,
    CountrySelect
  },
  data(){
    return {
      loading: false,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/Loading.gif')
    }
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData() {
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false
    }
  },
  async created(){
    const data = await this.fetchCovidData()
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries 
    this.loading = false 
  }
}
</script>
