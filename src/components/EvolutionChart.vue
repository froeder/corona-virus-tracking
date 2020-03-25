<template>
  <div>
    <GChart type="LineChart" :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { GChart } from "vue-google-charts";
import moment from "moment" ;

export default {
  name: "EvolutionChart",
  props: ["cases", "deaths"],
  components: {
    GChart
  },
  data() {
    return {
      datas: Object.keys(this.cases),
      valuesCases: Object.values(this.cases),
      valuesDeaths: Object.values(this.deaths),
      chartDatas: [["", "Casos", "Mortes"]],
      chartData: [],
      chartOptions: {
        colors: ['red', 'black'],
        legend: { position: 'bottom' },
        chart: {
          title: "Company Performance",
          subtitle: "Sales, Expenses, and Profit: 2014-2017"
        }
      }
    };
  },
  mounted() {
    const size = this.datas.length ;
    for(let i = 35 ; i < size ; i++){
      this.chartDatas.push([moment(this.datas[i]).format('DD/MM/YYYY'), parseInt(this.valuesCases[i]), parseInt(this.valuesDeaths[i])])
    }
    this.chartData = this.chartDatas
  }
};
</script>
