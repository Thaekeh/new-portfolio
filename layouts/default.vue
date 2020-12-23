<template>
  <v-app dark>
    <v-app-bar
      v-if="
        this.$vuetify.breakpoint.name === 'sm' ||
        this.$vuetify.breakpoint.name === 'xs'
      "
      color="secondary"
      flat
      fixed
    >
      <h2>TH</h2>
      <v-spacer></v-spacer>
      <v-app-bar-nav-icon
        @click="navigation = !navigation"
      ></v-app-bar-nav-icon>
    </v-app-bar>
    <v-navigation-drawer
      v-model="navigation"
      mini-variant
      fixed
      app
      floating
      color="primary"
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
                :href="social.to"
                target="_blank"
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
    <v-navigation-drawer
      id="navigation-drawer"
      mini-variant
      fixed
      app
      floating
      color="primary"
      mini-variant-width="65"
      mobile-breakpoint="960"
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
                :href="social.to"
                target="_blank"
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
    <v-main id="main" class="secondary">
      <v-container>
        <nuxt id="screen" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
export default {
  data() {
    return {
      navigation: false,
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
      ],
      socials: [
        {
          icon: 'mdi-linkedin',
          title: 'LinkedIn',
          to: 'https://www.linkedin.com/in/thaeke-hekkenberg/',
        },
        {
          icon: 'mdi-github',
          title: 'GitHub',
          to: 'https://github.com/Thaekeh',
        },
        {
          icon: 'mdi-stack-overflow',
          title: 'Stack Overflow',
          to: 'https://stackoverflow.com/users/14109713/thaeke-hekkenberg',
        },
        {
          icon: 'mdi-codepen',
          title: 'CodePen',
          to: 'https://codepen.io/thaekeh',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
#navigation-drawer {
  box-shadow: 5px 0 10px -2px #00000080;
}

#screen {
  margin-top: 30px;
}

.list-item {
  cursor: pointer;
  &:hover .icon {
    color: var(--v-purple-base) !important;
  }
}

.icon {
  color: rgba(255, 255, 255, 0.6) !important;
}

#social-list {
  bottom: 20px;
}
</style>
