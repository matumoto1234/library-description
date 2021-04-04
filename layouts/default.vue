<template>
  <v-app id="inspire">
    <!-- APP-BAR BEGIN HERE -->
    <v-app-bar
      app
      color="white"
      flat
    >
      <!-- V-TABS BEGIN HERE -->
      <v-tabs
        centered
        class="ml-n9"
        color="grey darken-1"
      >
        <v-tab href="/">TOP</v-tab>
        <v-tab href="https://github.com/matumoto1234/library">GITHUB</v-tab>
      </v-tabs>
      <!-- V-TABS END HERE -->
    </v-app-bar>
    <!-- APP-BAR END HERE-->

    <!-- CONTENTS BEGIN HERE -->
    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="4"
          >
            <v-sheet
              min-height="268"
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
            </v-sheet>
          </v-col>

          <v-col
            cols="12"
            sm="8"
          >
            <v-sheet
              min-height="100vh"
              rounded="lg"
            >
            <!-- DESCRIPTION BEGIN HERE -->
            <router-view>
            </router-view>
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
    menus: [
      {
        name: 'グラフ',
        subMenus: [
          {
            name: 'Dijkstra',
            path: '/dijkstra'
          },
          {
            name: 'Warshallfloyd',
            path: '/warshallfloyd'
          },
          {
            name: 'Bellmanford',
            path: '/bellmanford'
          }
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
