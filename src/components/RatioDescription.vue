<template>
  <v-col cols="auto">
    <v-dialog transition="dialog-bottom-transition" max-width="600">
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          class="
            ma-2
            font-navigation
            text-md-body-1 text-sm-button
            ml-md-5 ml-sm-3
          "
          color="yellow darken-4"
          v-bind="attrs"
          v-on="on"
          dark
        >
          黄金比率とは?<v-icon dark right>mdi-help-circle</v-icon>
        </v-btn>
      </template>
      <template v-slot:default="dialog">
        <v-card>
          <v-toolbar class="text-h6" color="amber darken-3" dark>黄金比率とは？</v-toolbar>
          <v-card-text>
            <p class="text-body-1 pa-2 pt-10">家計の黄金比率とは『はじめての人のための3000円投資生活』の著者であるファイナンシャルプランナーの横山光昭さんが考案した比率です。</p>
            <p class="text-body-1 pa-2">本アプリでは以下のサイトで紹介されている家計の割合を参考に計算を行っています。</p>
            <a class="text-body-1 pa-2" href="https://yurutsuma.com/the-golden-ratio-of-household/"  target="_blank" rel="noopener noreferrer">家計の黄金比率を使って予算作成に役立てよう！</a>
          </v-card-text>
          <v-card-actions class="justify-end">
            <v-btn text @click="dialog.value = false">Close</v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-dialog>
  </v-col>
</template>