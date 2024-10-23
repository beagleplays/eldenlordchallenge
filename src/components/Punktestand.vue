<template>
  <div>
    <button @click="sortParticipants">
      <i class="fas fa-sort-amount-up"></i> Sortieren nach Punktzahl
    </button>
    <ul>
      <li v-for="participant in participants" :key="participant.streamer">
        <h3>{{ participant.streamer }}</h3>
        <p>Aktuelle Punktzahl: {{ participant.score }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      participants: []
    };
  },
  created() {
    this.fetchParticipants();
  },
  methods: {
    fetchParticipants() {
      axios.get('/path/to/participants.json')
        .then(response => {
          this.participants = response.data;
        })
        .catch(error => {
          console.error('Error fetching participants:', error);
        });
    },
    sortParticipants() {
      this.participants.sort((a, b) => a.score - b.score);
    }
  }
};
</script>

<style scoped>
button {
  margin-bottom: 20px;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
}
</style>