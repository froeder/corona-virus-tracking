<template>
    <q-card style="background-color: rgba(255, 255, 255, 01)">
        <q-card-section>
            <div class="text-h6 text-center">Evolução dos casos </div>
            <div class="text-center text-subtitle2 text-weight-light">Desde o primeiro caso confirmado</div>
            <EvolutionChart v-bind:cases="cases"></EvolutionChart>
        </q-card-section>
    </q-card>
</template>

<script>
import EvolutionChart from "../components/EvolutionChart.vue"

export default {
    name: "Timeline",
    props: ['brazil'],
    components: {
        EvolutionChart
    } ,
    data(){
        return {
            cases: this.brazil[0].timeline.cases,
            deaths: this.brazil[0].timeline.deaths
        }
    }
}
</script>