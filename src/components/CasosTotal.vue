<template>
    <q-card>
      <q-card-section>
        <div class="text-h6 text-center">Casos no Brasil</div>
        <div class="text-subtitle-2 text-weight-thin text-center">
          Atualizado em: {{updated_at}}
        </div>
      </q-card-section>
      <q-card-section class="text-center">
        <div class="text-weight-regular badgeDiv">Confirmados:  <q-badge class="badge" color="red">{{latest.cases}}</q-badge></div> 
        <div class="text-weight-regular badgeDiv">Confirmados hoje: <q-badge class="badge" color="red">{{latest.todayCases}}</q-badge></div>
        <div class="text-weight-regular badgeDiv">Mortes: <q-badge class="badge" color="red">{{latest.deaths}}</q-badge></div>
        <div class="text-weight-regular badgeDiv">Mortes no dia: <q-badge class="badge" color="red">{{latest.todayDeaths}}</q-badge></div>
        <div class="text-weight-regular badgeDiv">Recuperados: <q-badge class="badge" color="red">{{latest.recovered}}</q-badge></div>
      </q-card-section>
    </q-card>
</template>

<script>
export default {
    name: "CasosTotal",
    props: ['updated_at', 'latest']
}
</script>

<style lang="stylus">
  .badge{
    padding:.5em ; 
    font-size:1em ;
    font-weight:900
  } 
  .badgeDiv{
    margin-top:1em
  }
</style>