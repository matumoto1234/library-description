<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <!-- MENU BEGIN HERE -->
      <v-subheader>Menu</v-subheader>
      <v-list expand>
        <v-list-group v-for="menu in menus" :key="menu.name" no-action>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>{{ menu.name }}</v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item v-for="sub in menu.subMenus" :key="sub.name" :to="sub.path">
            <v-list-item-title>
              {{ sub.name }}
            </v-list-item-title>
          </v-list-item>
        </v-list-group>
      </v-list>
      <!-- MENU END HERE -->
    </v-navigation-drawer>
    <!-- APP-BAR BEGIN HERE -->
    <v-app-bar
      app
      dense
      absolute
      color="white"
    >
      <v-app-bar-nav-icon left @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>
        library
      </v-toolbar-title>
      <!-- V-TABS BEGIN HERE -->
      <template v-slot:extension>
        <v-tabs
          class="ml-n9"
          color="grey darken-1"
          fixed-tabs
        >
          <v-tab href="/">
            TOP
          </v-tab>
          <v-tab href="https://github.com/matumoto1234/library">
            GITHUB
          </v-tab>
        </v-tabs>
      </template>
      <!-- V-TABS END HERE -->
    </v-app-bar>
    <!-- APP-BAR END HERE-->

    <!-- CONTENTS BEGIN HERE -->
    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="12"
          >
            <v-sheet
              min-height="100vh"
            >
              <!-- DESCRIPTION BEGIN HERE -->
              <router-view />
              <!-- DESCRIPTION END HERE -->
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <!-- CONTENTS END HERE -->
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    menus: [
      {
        name: 'グラフ',
        subMenus: [
          {
            name: 'Bellmanford',
            path: '/bellmanford'
          },
          {
            name: 'ConvertGraph',
            path: '/convertgraph'
          },
          {
            name: 'Dijkstra',
            path: '/dijkstra'
          },
          {
            name: 'GridBFS',
            path: '/gridbfs'
          },
          {
            name: 'LowLink',
            path: '/lowlink'
          },
          {
            name: 'ShortestHamiltonianCycle',
            path: '/shortesthamiltoniancycle'
          },
          {
            name: 'ShortestHamiltonianPath',
            path: '/shortesthamiltonianpath'
          },
          {
            name: 'StronglyConnectedComponent',
            path: '/stronglyconnectedcomponent'
          },
          {
            name: 'WarshallFloyd',
            path: '/warshallfloyd'
          },
          {
            name: 'Warshallfloyd',
            path: '/warshallfloyd'
          },
        ]
      },
      {
        name: 'データ構造',
        subMenus: [
          {
            name: 'Cumulative',
            path: 'Description'
          },
          {
            name: 'Cumulative2D',
            path: 'Description'
          }
        ]
      }
    ]
  })
}
</script>
