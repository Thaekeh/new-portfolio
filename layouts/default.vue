<template>
  <v-app dark>
    <v-navigation-drawer
      mini-variant
      fixed
      app
      floating
      color="primary"
      mini-variant-width="80"
    >
      <v-list>
        <v-tooltip
          v-for="(item, i) in items"
          :key="i"
          right
          transition="slide-x-transition"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-list-item
              :to="item.to"
              router
              exact
              v-bind="attrs"
              class="list-item"
              v-on="on"
            >
              <v-list-item-action class="list-item-action">
                <v-icon class="icon" size="30">{{ item.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title v-text="item.title" />
              </v-list-item-content>
            </v-list-item>
          </template>
          <span>{{ item.title }}</span>
        </v-tooltip>
      </v-list>
      <template v-slot:append>
        <v-list id="social-list">
          <v-tooltip
            v-for="(social, i) in socials"
            :key="i"
            right
            transition="slide-x-transition"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-list-item
                :to="social.to"
                router
                exact
                v-bind="attrs"
                class="list-item"
                v-on="on"
              >
                <v-list-item-action class="list-item-action">
                  <v-icon class="icon" size="25">{{ social.icon }}</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                  <v-list-item-title v-text="social.title" />
                </v-list-item-content>
              </v-list-item>
            </template>
            <span>{{ social.title }}</span>
          </v-tooltip>
        </v-list>
      </template>
    </v-navigation-drawer>
    <v-main class="secondary" id="main">
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
export default {
  data() {
    return {
      items: [
        {
          icon: 'mdi-account-hard-hat',
          title: 'My Work',
          to: '/',
        },
        {
          icon: 'mdi-code-tags',
          title: 'Code',
          to: '/code',
        },
        {
          icon: 'mdi-text-box-multiple-outline',
          title: 'Articles',
          to: '/inspire',
        },
      ],
      socials: [
        {
          icon: 'mdi-linkedin',
          title: 'Linked In',
          to: '',
        },
        {
          icon: 'mdi-github',
          title: 'GitHub',
          to: '',
        },
        {
          icon: 'mdi-stack-overflow',
          title: 'Stack Overflow',
          to: '',
        },
        {
          icon: 'mdi-codepen',
          title: 'CodePen',
          to: '',
        },
      ],
    }
  },
  mounted() {
    console.clear()
  },
}
</script>

<style lang="scss" scoped>
.list-item {
  cursor: pointer;
  &:hover .icon {
    color: #b629e5 !important;
  }
}

.icon {
  color: rgba(255, 255, 255, 0.6) !important;
}

#social-list {
  bottom: 20px;
}

// #main {
//   width: 90%;
// }
</style>
