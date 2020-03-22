<template>
  <q-page style="padding:1em">
    <div class="text-center" v-if="!loadedCases">
      <q-spinner size="5em" color="yellow"></q-spinner>
      <div class="text-weight-thin">
        Carregando dados
      </div>
    </div>
    <CasosTotal
      v-if="loadedCases"
      v-bind:updated_at="updated_at"
      v-bind:latest="latest"
    ></CasosTotal>
    <div style="margin-top:3em" class="text-center" v-if="!loadedHistorical">
      <q-spinner size="5em" color="yellow"></q-spinner>
      <div class="text-weight-thin">
        Carregando dados
      </div>
    </div>
    <Timeline v-if="loadedHistorical" style="margin-top:3em" v-bind:brazil="brazil"></Timeline>
  </q-page>
</template>

<script>
import axios from "axios";
import moment from "moment";
import CasosTotal from "../components/CasosTotal.vue";
import Timeline from "../components/Timeline.vue";

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
      updated_at: "",
      brazil: {},
      loadedCases: false,
      loadedHistorical: false
    };
  },
  methods: {
    async fetchLatest() {
      return await axios.get("https://corona.lmao.ninja/countries/brazil");
    },
    async fetchHistorical() {
      return await axios.get("https://corona.lmao.ninja/historical");
    },
    async formatDate(date) {
      return moment(date).format("DD/MM/YYYY");
    },
    async formatHistorical(historic) {
      return historic.filter(country => {
        return country.country === "Brazil";
      });
    }
  },
  async mounted() {
    this.fetch = await this.fetchLatest();
    this.latest = this.fetch.data;
    if (this.latest) {
      this.loadedCases = true;
    }
    this.historical = await this.fetchHistorical();
    this.brazil = await this.formatHistorical(this.historical.data);
    if (this.brazil) {
      this.loadedHistorical = true;
    }
    this.updated_at = await this.formatDate();
  }
};
</script>
