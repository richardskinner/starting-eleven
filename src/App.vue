<template>
    <div id="app">
        <div class="md-layout md-gutter">
            <div class="md-layout-item md-gutter">
                <img alt="Vue logo" src="./assets/logo.png">
            </div>
        </div>
        <div class="md-layout md-gutter">
            <div class="md-layout-item md-gutter">
                <Select :items="allFormations" :selected="selectFormation" :inital-value="formation"/>
            </div>
        </div>
        <div class="md-layout md-gutter">
            <div class="md-layout-item md-gutter">
                <h1 class="md-primary">Formation ({{ formation }})</h1>
            </div>
        </div>
        <div class="md-layout md-gutter">
            <div class="md-layout-item">
                <Pitch v-bind:formation="formation" />
            </div>
        </div>
    </div>
</template>

<script>
  import Select from "./components/Form/Select";
  import Pitch from "./components/Pitch.vue";

  import formations from "./data/formations";

  export default {
    name: 'App',
    components: {
      Pitch,
      Select
    },
    data: () => ({
      selectedFormation: null,
      allFormations: formations.modern_formations,
    }),
    computed: {
      formation() {
        return this.selectedFormation ?? this.allFormations[0]
      }
    },
    methods: {
      selectFormation(formation) {
        this.selectedFormation = formation
      }
    }
  }
</script>

<style lang="scss">
    #app {
        font-family: Roboto, 'Noto Sans', -apple-system, BlinkMacSystemFont, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        margin: 60px auto 0;
        display: block;
        width: 50%;
    }
</style>
