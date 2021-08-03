<template>
  <div id="app" class="font-sans">
    <h3 class="font-semibold text-gray-600">Vote Count App</h3>

    <div v-for="(candidate, index) in candidates" :key="index">
      <nominee-card
        :nominee="candidate.name"
        :srcImage="candidate.picture"
        :officeStatus="candidate.status"
        :voteCount="candidate.count"
        @voteNow ="addVote($event, index)"
      ></nominee-card>
    </div>
  </div>
</template>

<script>
import NomineeCard from "./components/NomineeCard.vue";

export default {
  name: "App",
  data() {
    return {
      candidates: [
        {
          picture: "gettyimages-509590596-web-1567541434.jpg",
          name: "Jane Done",
          status: "Incumbent Senator",
          count: 16,
        },
        {
          picture: "gettyimages-985138634-612x612.jpg",
          name: "John Done",
          status: "Challenger",
          count: 300,
        },
        {
          picture: "GettyImages-1092658864_hero-1024x575.jpg",
          name: "Joe Bloggs",
          status: "Challenger",
          count: 100,
        },
      ],
    };
  },

  components: {
    NomineeCard,
  },
  methods: {
    // $event data received from Nominee component
    addVote($event, index) {
      this.candidates[index].count = $event + 1
      console.log(this.candidates[index].name + "count is" + this.candidates[index].count)
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
