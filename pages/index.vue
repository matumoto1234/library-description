<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="10" md="6">
      <div class="text-center">
        <h1>HelloWorld</h1>
        <br>
        <v-btn
          dark
          color="blue"
          min-height="100"
          min-width="100"
          class="mx-2"
          fab
          href="https://twitter.com/matumoto_1234"
        >
          <v-icon dark size="70">
            mdi-twitter
          </v-icon>
        </v-btn>
        <v-btn
          dark
          min-height="100"
          min-width="100"
          fab
          href="https://github.com/matumoto1234"
        >
          <v-icon dark size="70">
            mdi-github
          </v-icon>
        </v-btn>
        <br>
        <br>
        <hr>
      </div>
      matumotoが作ったライブラリです。
      コピペなど自由です。
      <br>
      バグっていることもあるので信用しきらないでください。
      <br>
      バグを見つけたらTwitterなどで教えてくださるとありがたいです。
    </v-col>
  </v-row>
</template>

<script>
</script>

<style scoped>
h1 {
  font-size: 70px;
  position: relative;
  padding: 0.25em 1em;
  border-top: solid 2px black;
  border-bottom: solid 2px black;
}
h1:before, h1:after {
  content: '';
  position: absolute;
  top: -7px;
  width: 2px;
  height: -webkit-calc(100% + 14px);
  height: calc(100% + 14px);
  background-color: black;
}
h1:before {
  left: 7px;
}
h1:after {
  right: 7px;
}
</style>
