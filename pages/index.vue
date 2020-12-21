<template>
  <v-container id="container">
    <v-row>
      <h1 id="main-title">My Work</h1>
    </v-row>
    <v-row id="search-row" align="center">
      <v-col>
        <v-item-group id="type-selector" multiple>
          <v-item v-slot="{ active }"
            ><v-chip
              v-model="appTag"
              class="chip"
              active-class="purple--text"
              :input-value="active"
              @click="appTag = !appTag"
            >
              <v-avatar left>
                <v-icon>mdi-code-tags</v-icon>
              </v-avatar>
              Code
            </v-chip></v-item
          >
          <v-item v-slot="{ active }"
            ><v-chip
              v-model="articleTag"
              class="chip"
              active-class="purple--text"
              :input-value="active"
              @click="articleTag = !articleTag"
            >
              <v-avatar left>
                <v-icon>mdi-text</v-icon>
              </v-avatar>

              Article
            </v-chip></v-item
          >
        </v-item-group>
      </v-col>
      <v-col>
        <v-text-field
          v-model="searchQuery"
          placeholder="Search for a specific project"
          append-outer-icon="mdi-magnify"
          color="#750999"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row
      v-if="filteredItems.length != 0"
      id="item-row"
      justify="center"
      align="center"
    >
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
                    <v-btn class="button">{{ item.buttonTwo }}</v-btn>
                  </span>
                </v-overlay>
              </v-fade-transition>
            </v-card>
          </template>
        </v-hover>
      </v-col>
    </v-row>
    <v-row v-else id="empty-row" align="center">
      <v-col>
        <h2 id="no-result-title">
          Our Robot Detective Couldn't Find Anything <v-icon>mdi-robot</v-icon>
        </h2>
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
      emptyArray: false,
      items: [
        {
          title: 'Train That Brain',
          type: 'Web App',
          subtitle: 'Learning App For Autodidacts',
          image: 'ttb-cover.png',
          buttonTwo: 'Visit Site',
        },
        {
          title: 'UI Components',
          type: 'Chrome Extension',
          subtitle: 'Chrome Extension For Designing Components',
          image: 'ui-extension-cover.png',
          buttonTwo: 'Visit Extension',
        },
        {
          title: 'Working With Arrays In Vue.js',
          type: 'Article',
          subtitle: 'Medium Article',
          image: 'vue-array-article-cover.png',
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
          return item.type.includes('Article')
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
  @media screen and (min-width: 1265px) {
    min-height: 350px;
  }
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

#empty-row {
  text-align: center;
}

#no-result-title {
  margin-top: 30px;
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

.chip {
  font-weight: 500;
}
</style>
