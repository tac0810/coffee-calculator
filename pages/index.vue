<template>
  <div>
    <v-main>
      <v-container>
        <v-row dense>
          <v-col cols="12">
            <v-card>
              <v-card-title>
                <v-icon color="#0288D1" large left> mdi-water </v-icon>
                <span class="title font-weight-light">Filter Calc</span>
              </v-card-title>
              <v-card-text>
                好きな粉の量、飲みたい量に合わせてを美味しくドリップするための計算
              </v-card-text>
              <v-card-actions>
                <v-btn text to="/filter" color="#0288D1"> Drip Now </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card>
              <v-card-title>
                <v-icon color="#F57C00" large left>mdi-fire</v-icon>
                <span class="title font-weight-light">Roasting Calc</span>
              </v-card-title>
              <v-card-text>豆をブレンドする際の比率計算</v-card-text>
              <v-card-actions>
                <v-btn text to="/roast" color="#F57C00"> Roast Now </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </div>
</template>