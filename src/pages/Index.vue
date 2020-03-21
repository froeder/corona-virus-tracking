<template>
  <q-page style="padding:1em">
    <CasosTotal v-bind:updated_at="updated_at" v-bind:latest="latest"></CasosTotal>
  </q-page>
</template>

<script>
import axios from "axios";
import moment from "moment"
import CasosTotal from "../components/CasosTotal.vue"

export default {
  name: "PageIndex",
  components: {
    CasosTotal
  },
  data() {
    return {
      fetch: {},
      latest: {},
      updated_at: ''
    };
  },
  methods: {
    async fetchBrasil(){
      return await axios.get('https://coronavirus-tracker-api.herokuapp.com/v2/locations/35')
    },
    async formatDate(date){
      return moment(date).format("DD/MM/YYYY")
    }
  },
  async mounted() {
    this.fetch = await this.fetchBrasil()
    let dateTemp = await this.fetch.data.location.last_updated
    this.updated_at = await this.formatDate(dateTemp) ;
    this.latest = this.fetch.data.location.latest
  }
};
</script>
