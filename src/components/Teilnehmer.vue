<template>
  <div class="table">
    <v-container fluid>
    <v-row dense v-for="streamer in participantList" :key="streamer.name">
      <v-col>
        <v-avatar
          size="70px"
        >
        <a color="primary"  :href="`${streamer.url}`" target="_blank">
        <img v-bind:src="streamer.image" height="70px" width="70px">
        </a>
        </v-avatar>
        
      </v-col>
      <v-col>
          <v-card
          :title="`${streamer.name}`"
          :text="`Aktueller Punktestand:` +` `+`${streamer.score}`"
          :href="`${streamer.url}`"
          target="_blank"
          ></v-card>
      </v-col>
      <v-col>
        <a color="primary"  :href="`${streamer.url}`" target="_blank">
          <v-img
            :width="60"
            aspect-ratio="16/9"
            cover
            src="../assets/twlogo.png"
          ></v-img>
        </a >
      </v-col>
    </v-row>
    </v-container>
  </div>
</template>

<script>
  import participants from '../../participants.json'
  export default {
    data() {
        return {
          participantList: participants,
        }
    }
  }
</script>
<style>
.table{
  padding: 50px
}
</style>
