<template>
    <div id="pitch-wrapper">
        <div id="pitch" :style="pitchRatio">
            <div v-for="player in players" :key="player.index">
                <div>Players in row {{ player }}</div>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    name: "Pitch",
    props: {
      formation: String
    },
    data: () => ({
      pitchRatio: ''
    }),
    computed: {
      players() {
        return this.formation.split("-")
      }
    },
    methods: {
      calculatePitchRatio() {
        const height = 120;
        const width = 80;

        const ratio = height / width;

        return 538 * ratio // @TODO: 538 is the width of the #pitch div, need to make dynamic in future
      }
    },
    mounted() {
      this.pitchRatio = "height: " + this.calculatePitchRatio() + "px"
    }
  }
</script>

<style lang="scss">
    #pitch {
        background-color: #1b3800;
        border: 5px solid white;
    }
</style>
