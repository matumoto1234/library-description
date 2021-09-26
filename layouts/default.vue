<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      width="550"
      disable-route-watcher
      temporary
      app
    >
      <!-- MENU BEGIN HERE -->
      <v-subheader>Menu</v-subheader>
      <v-list expand>
        <v-list-group v-for="menu in menus" :key="menu.name" no-action>
          <template #activator>
            <v-list-item-content>
              <v-list-item-title>{{ menu.name }}</v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item v-for="sub in menu.subMenus" :key="sub.name" :to="sub.path">
            <v-list-item-title>
              {{ sub.janame }}({{ sub.enname }})
            </v-list-item-title>
          </v-list-item>
        </v-list-group>
      </v-list>
      <!-- MENU END HERE -->
    </v-navigation-drawer>

    <!-- APP-BAR BEGIN HERE -->
    <v-app-bar
      dense
      app
      :absolute="isAbsolute"
      elevation="0"
      color="light-blue"
    >
      <v-app-bar-nav-icon
        left
        color="white"
        @click="drawer = !drawer"
      />
      <v-toolbar-title>
        <v-btn
          :ripple="false"
          to="/"
          plain
          nuxt
          text
          color="white"
          style="text-transform: none !important;"
        >
          Library
        </v-btn>
      </v-toolbar-title>

      <v-spacer />

      <v-btn icon @click="isAbsolute = !isAbsolute">
        <v-icon v-if="isAbsolute" color="white">
          mdi-pin-outline
        </v-icon>
        <v-icon v-else color="white">
          mdi-pin
        </v-icon>
      </v-btn>
    </v-app-bar>
    <!-- APP-BAR END HERE-->

    <!-- CONTENTS BEGIN HERE -->
    <v-main>
      <v-container>
        <v-col
          style="width:100%"
        >
          <v-sheet
            min-height="100vh"
          >
            <!-- DESCRIPTION BEGIN HERE -->
            <router-view />
            <!-- DESCRIPTION END HERE -->
          </v-sheet>
        </v-col>
      </v-container>
    </v-main>
    <!-- CONTENTS END HERE -->
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    isAbsolute: false,
    isCollapse: false,
    menus: [
      {
        name: 'データ構造',
        subMenus: [
          {
            janame: '二分探索',
            enname: 'BinarySearch',
            path: 'binarysearch'
          },
          {
            janame: '累積和',
            enname: 'CumulativeSum',
            path: 'cumulativesum'
          },
          {
            janame: '二次元累積和',
            enname: 'CumulativeSum2D',
            path: 'cumulativesum2d'
          },
          {
            janame: 'セグメントツリー',
            enname: 'SegmentTree',
            path: 'segmenttree'
          },
          {
            janame: '素集合データ構造',
            enname: 'UnionFind',
            path: 'unionfind'
          },
          {
            janame: '重み付き素集合データ構造',
            enname: 'WeightedUnionFind',
            path: 'weightedunionfind'
          }
        ]
      },
      {
        name: '動的計画法',
        subMenus: [
          {
            janame: '最長共通部分列',
            enname: 'LongestCommonSubsequence',
            path: 'longestcommonsubsequence'
          }
        ]
      },
      {
        name: '幾何',
        subMenus: [
          {
            janame: '二次元上の点',
            enname: 'Point',
            path: 'point'
          }
        ]
      },
      {
        name: 'グラフ',
        subMenus: [
          {
            janame: '単一始点最短経路',
            enname: 'Bellmanford',
            path: '/bellmanford'
          },
          {
            janame: '単一始点最短経路',
            enname: 'Dijkstra',
            path: '/dijkstra'
          },
          {
            janame: '単一始点最短経路',
            enname: 'WarshallFloyd',
            path: '/warshallfloyd'
          },
          {
            janame: '橋/間接点の列挙',
            enname: 'LowLink',
            path: '/lowlink'
          },
          {
            janame: 'トポロジカルソート',
            enname: 'TopologicalSort',
            path: '/topologicalsort'
          },
          {
            janame: '強連結成分分解',
            enname: 'StronglyConnectedComponent',
            path: '/stronglyconnectedcomponent'
          },
          {
            janame: '最短ハミルトン閉路',
            enname: 'ShortestHamiltonianCycle',
            path: '/shortesthamiltoniancycle'
          },
          {
            janame: '最短ハミルトン経路',
            enname: 'ShortestHamiltonianPath',
            path: '/shortesthamiltonianpath'
          },
          {
            janame: 'グラフ変換',
            enname: 'ConvertGraph',
            path: '/convertgraph'
          },
          {
            janame: 'グリッドグラフ上の幅優先探索',
            enname: 'GridBFS',
            path: '/gridbfs'
          }
        ]
      },
      {
        name: '数学',
        subMenus: [
          {
            janame: '切り上げ除算',
            enname: 'CeilDivision',
            path: 'ceildiv'
          },
          {
            janame: '二項係数',
            enname: 'Binomial',
            path: 'binomial'
          },
          {
            janame: '約数列挙',
            enname: 'Divisor',
            path: 'divisor'
          },
          {
            janame: '素因数列挙',
            enname: 'PrimeFactor',
            path: 'primefactor'
          },
          {
            janame: 'オイラーのφ関数',
            enname: 'EulerPhi',
            path: 'eulerphi'
          },
          {
            janame: '拡張ユークリッドの互除法',
            enname: 'ExtendedEuclideanAlgorithm',
            path: 'extgcd'
          },
          {
            janame: '合同式での逆元',
            enname: 'ModInverse',
            path: 'modinv'
          },
          {
            janame: '合同式でのべき乗',
            enname: 'ModPower',
            path: 'modpow'
          },
          {
            janame: 'べき乗',
            enname: 'Power',
            path: 'pow'
          },
          {
            janame: 'エラトステネスの篩',
            enname: 'Sieve of Eratosthenes',
            path: 'sieve'
          },
          {
            janame: '最小素因数分解',
            enname: 'SmallestPrimeFactor',
            path: 'smallestprimefactor'
          }
        ]
      },
      {
        name: '文字列',
        subMenus: [
          {
            janame: 'ローリングハッシュ',
            enname: 'RollingHash',
            path: 'rollinghash'
          },
          {
            janame: '二次元ローリングハッシュ',
            enname: 'RollingHash2D',
            path: 'rollinghash2d'
          },
          {
            janame: '連続部分文字列',
            enname: 'Substring',
            path: 'substr'
          }
        ]
      },
      {
        name: 'その他',
        subMenus: [
          {
            janame: '座標圧縮',
            enname: 'Compress',
            path: 'compress'
          }
        ]
      }
    ]
  })
}
</script>
