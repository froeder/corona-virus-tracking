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
  props: ["cases"],
  components: {
    GChart
  },
  data() {
    return {
      datas: Object.keys(this.cases),
      values: Object.values(this.cases),
      chartDatas: [["", "Casos"]],
      chartData: [],
      chartOptions: {
        colors: ['red'],
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
      this.chartDatas.push([moment(this.datas[i]).format('DD/MM/YYYY'), parseInt(this.values[i])])
    }
    this.chartData = this.chartDatas
  }
};
</script>
