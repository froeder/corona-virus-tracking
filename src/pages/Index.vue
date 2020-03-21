<template>
  <q-page style="padding:1em">
    <CasosTotal v-bind:updated_at="updated_at" v-bind:latest="latest"></CasosTotal>
  </q-page>
</template>

<script>
import axios from "axios";
import moment from "moment"
import CasosTotal from "../components/CasosTotal.vue"
import Timeline from "../components/Timeline.vue"

export default {
  name: "PageIndex",
  components: {
    CasosTotal,
    Timeline
  },
  data() {
    return {
      fetch: {},
      latest: {},
      historical: {},
      updated_at: ""
    };
  },
  methods: {
    async fetchLatest(){
      return await axios.get('https://corona.lmao.ninja/countries/brazil')
    },
    async fetchHistorical(){
      return await axios.get('https://corona.lmao.ninja/historical')
    },
    async formatDate(date){
      return moment(date).format("DD/MM/YYYY")
    },
    formatHistorical(historic){
      let brazil = historic.filter(country => {
        return country.country === 'Brazil'
      })

      console.log(brazil)
    }
  },
  async mounted() {
    this.fetch = await this.fetchLatest()
    this.historical = await this.fetchHistorical() ;
    this.formatHistorical(this.historical.data)
    this.updated_at = this.formatDate(new Date()) ;
  }
};
</script>
