<template>
    <q-card style="background-color:rgba(255,0,0,0.2)">
      <q-card-section>
        <div class="text-h6 text-center">Casos no Brasil</div>
        <div class="text-subtitle-2 text-weight-thin text-center">
          Atualizado em: {{updated_at}}
        </div>
      </q-card-section>
      <q-card-section>
        <div class="text-h6">Últimos casos</div>
        <div class="text-weight-regular">Confirmados: <strong>{{latest.confirmed}}</strong></div>
        <div class="text-weight-regular">Mortes: <strong>{{latest.deaths}}</strong></div>
        <div class="text-weight-regular">Recuperados: <strong>{{latest.recovered}}</strong></div>
      </q-card-section>
    </q-card>
</template>

<script>
export default {
    name: "CasosTotal",
    props: ['updated_at', 'latest']
}
</script>