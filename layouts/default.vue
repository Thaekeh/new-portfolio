<template>
  <v-app dark>
    <v-navigation-drawer mini-variant fixed app floating color="primary">
      <v-list>
        <v-tooltip
          v-for="(item, i) in items"
          :key="i"
          right
          transition="slide-x-transition"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-list-item :to="item.to" router exact v-bind="attrs" v-on="on">
              <v-list-item-action>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title v-text="item.title" />
              </v-list-item-content>
            </v-list-item>
          </template>
          <span>{{ item.title }}</span>
        </v-tooltip>
      </v-list>
    </v-navigation-drawer>
    <v-main class="secondary">
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
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
    }
  },
}
</script>
