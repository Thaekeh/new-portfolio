<template>
  <v-container id="container">
    <v-row align="center" justify="center">
      <h1>A short history of me</h1>
      <v-timeline>
        <v-timeline-item
          v-for="(item, index) in timelineItems"
          :key="index"
          left
          :color="item.color"
          fill-dot
        >
          <template v-slot:opposite>
            <span
              :class="`headline font-weight-bold ${item.color}--text`"
              v-text="item.year"
            ></span>
            <div class="py-4">
              <h2
                :class="`headline font-weight-light mb-4 ${item.color}--text`"
              >
                {{ item.title }}
              </h2>
              <div>
                Lorem ipsum dolor sit amet, no nam oblique veritus. Commune
                scaevola imperdiet nec ut, sed euismod convenire principes at.
                Est et nobis iisque percipit, an vim zril disputando
                voluptatibus, vix an salutandi sententiae.
              </div>
            </div></template
          ></v-timeline-item
        >
      </v-timeline>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      timelineItems: [
        { year: 1029, title: 'Stuff', color: 'red' },
        { year: 1997, title: 'Born in the Netherlands', color: 'blue' },
      ],
    }
  },
})
</script>

<style lang="scss" scoped>
#container {
  text-align: center;
}
</style>
