<template>
    <div id="select-container">
        <md-field>
            <label for="formation">Select Formation</label>
            <md-select v-model="selectedValue" id="formation" name="formation">
                <md-option v-for="item in items" :key="item" :value="item">{{ item }}</md-option>
            </md-select>
        </md-field>
    </div>
</template>

<script>
  export default {
    name: "Select",
    props: {
      items: Array,
      selected: Function,
      initalValue: String
    },
    computed: {
      selectedValue: {
        get: function () {
          return this.initalValue
        },
        set: function (value) {
          this.selected(value)
          return value
        }
      }
    }
  }
</script>

<style lang="sass">

</style>
