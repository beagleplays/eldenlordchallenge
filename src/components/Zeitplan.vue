<template>
  <v-container fluid>

    <h1>Folgende Livestreams:</h1> 
    <v-select
      v-model="scheduleSelect"
      :items="availableStreamer"
      label="Suche deinen Streamer"
      ></v-select>
    <v-row dense v-for="entry in scheduleList" :key="entry.streamer">
      <v-card
    v-if="!scheduleSelect || scheduleSelect === 'Alle' || entry.streamer === scheduleSelect"
     class="mx-auto"
    :prepend-avatar="`${ entry.image }`"
    :subtitle="`${ entry.streamer }`"
    width="500"
    :title="`${ entry.description }`"
    :text="`${ entry.date }`+` `+`${ entry.time }`"
    :href="`${ entry.url }`"
    target="_blank"
  >



    <template v-slot:actions>
      <v-btn
        append-icon="mdi-chevron-right"
        color="purple-lighten-2"
        text="Zum Kanal"
        variant="outlined"
        block
        :href="`${ entry.url }`"
        target="_blank"
      ></v-btn>

      <v-divider></v-divider>
      
    </template>
  </v-card>
</v-row>
</v-container>

<v-checkbox
      v-model="showContainer"
      label="Vergangene Livestreams"
    ></v-checkbox>

<v-container fluid
v-if="showContainer">

<h1>Vergangene Livestreams:</h1>
<v-select
      v-model="pastScheduleSelect"
      :items="pastAvailableStreamer"
      label="Suche deinen Streamer"
      ></v-select>
<v-row dense v-for="entry in pastScheduleList" :key="entry.streamer">

  <v-card
  v-if="!pastScheduleSelect || pastScheduleSelect === 'Alle' || entry.streamer === pastScheduleSelect"
class="mx-auto"
:prepend-avatar="`${ entry.image }`"
:subtitle="`${ entry.streamer }`"
width="500"
:title="`${ entry.description }`"
:text="`${ entry.date }`+` `+`${ entry.time }`"
:href="`${ entry.url }`"
target="_blank"
>



<template v-slot:actions>
  <v-btn
    append-icon="mdi-chevron-right"
    color="purple-lighten-2"
    text="Zum Kanal"
    variant="outlined"
    block
    :href="`${ entry.url }`"
    target="_blank"
  ></v-btn>

  <v-divider></v-divider>
  
</template>
</v-card>
</v-row>
</v-container>

</template>

<script>
  import { VCardTitle } from 'vuetify/components';
import participants from '../../participants.json'
  import schedule from '../schedule.json'
  import pastSchedule from '../past-schedule.json'

export default {

  data() {
    return {
      scheduleSelect: 'Alle',
      pastScheduleSelect: 'Alle',
      scheduleList:schedule,
      pastScheduleList: pastSchedule,
      availableStreamer: [],
      pastAvailableStreamer: [],
      showContainer: false // Initialisiere die Checkbox als nicht aktiviert


    }
  },
  
  created() {
    this.availableStreamer = this.scheduleList.map(item => item.streamer);
    this.availableStreamer.unshift("Alle");

    this.pastAvailableStreamer = this.pastScheduleList.map(item => item.streamer);
    this.pastAvailableStreamer.unshift("Alle");
  }
}

</script>

<style>
h1 {
  text-align: center;
  padding: 26px;
}
</style>
