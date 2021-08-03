<template>
  <div>

    <div class="flex mt-8">
      <div class="ml-12 p-4 border-4 rounded-md">
        <img
          class="
            shadow-lg
            rounded-full
            max-w-full
            h-auto
            align-middle
            border-none"

          :src="require(`@/assets/${srcImage}`)"         
          alt="Candidate_Photo"
          height="80px"
          width="80px"
        />
      </div>

      <div class="flex flex-col justify-start items-baseline  w-1/4 p-15 border-4 rounded-md" >
        <h4 class="pt-4 pl-8 font-semibold text-gray-600">{{ nominee }}</h4>
        <p class="pl-8 font-semibold text-gray-600">{{ officeStatus }}</p>
      </div>
      <div class="w-32 p-15 border-4 rounded-md" @click="clickCounter()">
        <p class="pt-4 font-semibold text-gray-600">{{ voteCount }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NomineeCard",
  props: {
    nominee: String,
    srcImage: String,
    officeStatus: String,
    voteCount: Number,
  },
  methods: {
    clickCounter() {
       
       this.$emit('voteNow', this.voteCount)
    }   
  }

  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
