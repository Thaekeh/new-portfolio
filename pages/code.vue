<template>
  <v-row>
    <v-col class="text-center">
      <div class="code-container">
        <h2 class="pen-title">
          Sorting, Filtering, and Searching Arrays With Vue
        </h2>
        <v-card color="secondary" flat>
          <v-progress-circular
            v-if="loader"
            id="loader"
            size="50"
            indeterminate
            color=""
          ></v-progress-circular>
          <p
            class="codepen"
            data-height="387"
            data-theme-id="dark"
            data-default-tab="js,result"
            data-user="thaekeh"
            data-slug-hash="PoGJRKQ"
            data-preview="true"
            style="
              height: 387px;
              box-sizing: border-box;
              display: flex;
              align-items: center;
              justify-content: center;
              border: 2px solid;
              margin: 1em 0;
              padding: 1em;
            "
            data-pen-title="Sorting arrays with Vue - Medium"
          >
            <span
              >See the Pen
              <a href="https://codepen.io/thaekeh/pen/PoGJRKQ">
                Sorting arrays with Vue - Medium</a
              >
              by Thaekeh (<a href="https://codepen.io/thaekeh">@thaekeh</a>) on
              <a href="https://codepen.io">CodePen</a>.</span
            >
          </p>
          <script
            async
            src="https://cpwebassets.codepen.io/assets/embed/ei.js"
          ></script>
        </v-card>
      </div>
      <div class="code-container">
        <h2 class="pen-title">Pomodoro timer made with React</h2>
        <v-card color="secondary" flat>
          <v-progress-circular
            v-if="loader"
            id="loader"
            size="50"
            indeterminate
            color=""
          ></v-progress-circular>
          <p
            class="codepen"
            data-height="265"
            data-theme-id="dark"
            data-default-tab="js,result"
            data-user="thaekeh"
            data-slug-hash="MWjjOLx"
            data-preview="true"
            style="
              height: 265px;
              box-sizing: border-box;
              display: flex;
              align-items: center;
              justify-content: center;
              border: 2px solid;
              margin: 1em 0;
              padding: 1em;
            "
            data-pen-title="FCC - Pomodoro Timer"
          >
            <span
              >See the Pen
              <a href="https://codepen.io/thaekeh/pen/MWjjOLx">
                FCC - Pomodoro Timer</a
              >
              by Thaekeh (<a href="https://codepen.io/thaekeh">@thaekeh</a>) on
              <a href="https://codepen.io">CodePen</a>.</span
            >
          </p>
          <script
            async
            src="https://cpwebassets.codepen.io/assets/embed/ei.js"
          ></script>
        </v-card>
      </div>
    </v-col>
  </v-row>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      loader: true,
    }
  },
  mounted() {
    setTimeout(() => {
      this.loader = false
    }, 2000)
  },
})
</script>

<style lang="scss" scoped>
.code-container {
  margin-top: 50px;
}

.pen-title {
  margin-bottom: 10px;
  @media screen and (max-width: 640px) {
    font-size: 14px;
  }
}

#loader {
  top: 45%;
  position: absolute;
}
</style>
