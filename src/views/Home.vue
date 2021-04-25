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

  <CountrySelect :countries="countries" />
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
    }
  },
  async created(){
    const data = await this.fetchCovidData();
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries 
    this.loading = false 
  }
}
</script>
