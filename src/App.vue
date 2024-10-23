<template>

  <v-card>
    <div class="fixed-card">
    <v-tabs
      v-model="tab"
      bg-color="deep-purple"
    >
      <v-tab value="one" class="justify-center">Teilnehmer</v-tab>
      <v-tab value="two" class="justify-center">Zeitplan</v-tab>
    </v-tabs>
  </div>

    <v-card-text>
      <v-tabs-window v-model="tab">
        <v-tabs-window-item value="one">
          <Teilnehmer />
        </v-tabs-window-item>

        <v-tabs-window-item value="two">
          <Zeitplan />
        </v-tabs-window-item>
      </v-tabs-window>
    </v-card-text>
  </v-card>
</template>

<script>
  import Zeitplan from './components/Zeitplan.vue';
  import Teilnehmer from './components/Teilnehmer.vue';

  export default {

    components: {
      Zeitplan,
      Teilnehmer,
    },
    data: () => ({
      tab: null,
    }),
  }
</script>
<style>
.fixed-card {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  }
</style>