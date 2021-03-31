<template>
  <div>
    <v-toolbar flat color="#F57C00" dark>
      <v-btn icon to="/">
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-toolbar-title>Roasting Calc</v-toolbar-title>
    </v-toolbar>
    <v-main>
      <v-container>
        <v-form :model="form" class="pt-6">
          <v-row justify="center">
            <v-col cols="5">
              <v-text-field
                dense
                v-model="form.amountA"
                label="A豆(g)"
                type="number"
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
            <v-col cols="5">
              <v-text-field
                dense
                v-model="form.amountB"
                label="B豆(g)"
                type="number"
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-subheader class="pl-0">A豆の比率(%)</v-subheader>
              <v-slider
                dense
                v-model="form.ratio"
                thumb-label="always"
              ></v-slider>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-text-field
                dense
                v-model="100 - form.ratio"
                label="B豆の比率(%)"
                type="number"
                readonly
                style="pointer-events: none"
              >
                <template slot="append">%</template>
              </v-text-field>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-divider />
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-text-field
                :value="form.amountA * (100 - form.ratio) * 0.01"
                label="必要なB豆の量"
                type="number"
                readonly
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-text-field
                :value="
                  Math.min(
                    form.amountB - form.amountA * (100 - form.ratio) * 0.01,
                    0
                  )
                "
                label="足りないB豆の量"
                type="number"
                readonly
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
          </v-row>
        </v-form>
      </v-container>
    </v-main>
  </div>
  <!--  <el-container>
    <el-col :span="20" :offset="2">
      <el-form :model="form" label-width="120px">

        <el-form-item label="B豆の量">
          {{ form.amountA * (100 - form.ratio) * 0.01 }}g
        </el-form-item>
        <el-form-item label="足りないB豆の量">
          {{
            Math.min(
              form.amountB - form.amountA * (100 - form.ratio) * 0.01,
              0
            )
          }}g
        </el-form-item>
      </el-form>
    </el-col>
  </el-container>-->
</template>

<script>
export default {
  data() {
    return {
      form: {
        ratio: 100,
        amountA: 0,
        amountB: 0,
      },
    }
  },
}
</script>

<style scoped></style>
