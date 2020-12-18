<template>
  <v-container>
    <v-row>
      <h1 id="main-title">My Projects</h1>
    </v-row>
    <v-row justify="center" align="center">
      <v-col v-for="item in items" :key="item.title" cols="12" sm="8" md="4">
        <v-hover>
          <template v-slot:default="{ hover }">
            <v-card id="item-card" hover color="primary">
              <v-img :src="item.image"></v-img>
              <v-card-title class="card-title">{{ item.title }}</v-card-title>
              <v-card-subtitle>{{ item.subtitle }}</v-card-subtitle>
              <v-fade-transition>
                <v-overlay v-if="hover" absolute color="#750999">
                  <v-btn>Read Article</v-btn>
                </v-overlay>
              </v-fade-transition>
            </v-card>
          </template>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Working with arrays in Vue.js',
          type: 'Article',
          subtitle: 'Description',
          image: 'vue-array-article-cover.png',
        },
        {
          title: 'Working With CSV Files',
          type: 'Article',
          subtitle: 'Description',
          image: 'csv-article-cover.png',
        },
        {
          title: 'Netlify Environment Variables',
          type: 'Article',
          subtitle: 'Description',
          image: 'environment-variables-article-cover.png',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
#item-card {
  transition: all 300ms;
  &:hover {
    transform: translateY(-3px);
  }
}

#main-title {
  margin-bottom: 20px;
}

.card-title {
  font-weight: 600;
}
</style>
