<template>
  <v-container id="container">
    <v-row>
      <h1 id="main-title">My Projects</h1>
    </v-row>
    <v-row id="search-row" align="center">
      <v-col>
        <v-item-group id="type-selector" multiple>
          <v-item v-slot="{ active }"
            ><v-chip
              active-class="purple--text"
              :input-value="active"
              @click="appTag = !appTag"
              v-model="appTag"
            >
              App
            </v-chip></v-item
          >
          <v-item v-slot="{ active }"
            ><v-chip
              active-class="purple--text"
              :input-value="active"
              @click="articleTag = !articleTag"
              v-model="articleTag"
            >
              Article
            </v-chip></v-item
          >
        </v-item-group>
      </v-col>
      <v-col>
        <v-text-field
          placeholder="Search for a specific project"
          v-model="searchQuery"
          append-outer-icon="mdi-magnify"
          color="#750999"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row id="item-row" justify="center" align="center">
      <v-col
        v-for="item in filteredItems"
        :key="item.title"
        cols="12"
        sm="8"
        md="4"
      >
        <v-hover>
          <template v-slot:default="{ hover }">
            <v-card id="item-card" hover color="primary">
              <v-img :src="item.image"></v-img>
              <v-card-title class="card-title">{{ item.title }}</v-card-title>
              <v-card-subtitle>{{ item.subtitle }}</v-card-subtitle>
              <v-fade-transition>
                <v-overlay v-if="hover" absolute color="#750999">
                  <v-btn v-if="item.type === 'Article'">Read Article</v-btn>
                  <span v-else class="button-span">
                    <v-btn class="button">Learn More</v-btn>
                    <v-btn class="button">Visit Site</v-btn>
                  </span>
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
      searchQuery: '',
      appTag: true,
      articleTag: true,
      items: [
        {
          title: 'Train That Brain',
          type: 'Web App',
          subtitle: 'Learning App For Autodidacts',
          image: 'ttb-cover.png',
        },
        {
          title: 'Working With Arrays In Vue.js',
          type: 'Article',
          subtitle: 'Medium Article',
          image: 'vue-array-article-cover.png',
          buttonText: 'Read Article',
        },
        {
          title: 'Working With CSV Files',
          type: 'Article',
          subtitle: 'Medium Article',
          image: 'csv-article-cover.png',
        },
        {
          title: 'Netlify Environment Variables',
          type: 'Article',
          subtitle: 'Medium Article',
          image: 'environment-variables-article-cover.png',
        },
      ],
    }
  },
  computed: {
    filteredItems() {
      let tempArray = this.items

      if (!this.articleTag) {
        tempArray = tempArray.filter((item) => {
          return !item.type.includes('Article')
        })
      }

      if (!this.appTag) {
        tempArray = tempArray.filter((item) => {
          return !item.type.includes('App')
        })
      }

      if (this.searchQuery !== '' && this.searchQuery) {
        tempArray = tempArray.filter((item) => {
          return item.title
            .toUpperCase()
            .includes(this.searchQuery.toUpperCase())
        })
      }

      return tempArray
    },
  },
}
</script>

<style lang="scss" scoped>
#container {
  max-width: 90vw;
}

#item-card {
  min-height: 300px;
  margin: 5px;
  border-radius: 10px;
  transition: all 300ms;
  &:hover {
    transform: translateY(-3px);
  }
}

#main-title {
  margin-bottom: 20px;
}

.card-title {
  word-break: break-word;
  font-weight: 600;
  @media screen and (max-width: 1500px) {
    font-size: 18px;
  }
  @media screen and (max-width: 1200px) {
    font-size: 16px;
  }
}

.button-span {
  display: flex;
  flex-direction: column;
}

.button {
  margin: 10px;
}
</style>
