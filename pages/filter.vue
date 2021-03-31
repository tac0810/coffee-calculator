<template>
  <div>
    <v-toolbar flat color="#0288D1" dark>
      <v-btn icon to="/">
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-toolbar-title>Filter Calc</v-toolbar-title>
    </v-toolbar>
    <v-main>
      <v-container>
        <v-form :model="form" class="pt-6">
          <v-row justify="center">
            <v-col cols="5">
              <v-text-field
                dense
                v-model="form.water"
                label="お湯の量(g)"
                type="number"
                @input="onChange('coffee', $event)"
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
            <v-col cols="5">
              <v-text-field
                dense
                v-model="form.coffee"
                label="粉の量(g)"
                type="number"
                @input="onChange('water', $event)"
              >
                <template slot="append">g</template>
              </v-text-field>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-divider />
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="5">
              <span class="caption">1投目 - 20% (蒸らし)</span>
            </v-col>
            <v-col cols="5">
              <div class="text-h5 text-right">
                {{ form.water * 0.2 }} <span class="text-body-1">g</span>
              </div>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="5">
              <span class="caption">2投目 - 40%</span>
            </v-col>
            <v-col cols="5">
              <div class="text-h5 text-right">
                {{ form.water * 0.4 }} <span class="text-body-1">g</span>
              </div>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="5">
              <span class="caption">3投目 - 60%</span>
            </v-col>
            <v-col cols="5">
              <div class="text-h5 text-right">
                {{ form.water * 0.6 }} <span class="text-body-1">g</span>
              </div>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="5">
              <span class="caption">4投目 - 100%</span>
            </v-col>
            <v-col cols="5">
              <div class="text-h5 text-right">
                {{ form.water }} <span class="text-body-1">g</span>
              </div>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <v-divider />
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="10">
              <p class="text-sub-title-1 font-weight-bold">
                お湯と粉の比率
                <span class="text-body-2">(デフォルトは 100 : 8)</span>
              </p>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="4">
              <v-text-field
                dense
                v-model="base.water"
                label="お湯 (100固定)"
                type="number"
                readonly
                style="pointer-events: none"
              >
              </v-text-field>
            </v-col>
            <v-col cols="2">
              <p class="text-h6 text-center font-weight-black">:</p>
            </v-col>
            <v-col cols="4">
              <v-text-field
                dense
                v-model="base.coffee"
                label="粉"
                type="number"
                @input="onChangeRatio('coffee', $event)"
              >
              </v-text-field>
            </v-col>
          </v-row>
        </v-form>
      </v-container>
    </v-main>
  </div>
</template>

<script>
export default {
  computed: {
    ratioWater(){
      return this.base.water / this.base.coffee
    },
    ratioCoffee(){
      return this.base.coffee / this.base.water
    },
  },
  data() {
    return {
      form: {
        water: 150,
        coffee: 8,
      },
      base: {
        water: 100,
        coffee: 8,
      },
    }
  },
  mounted() {
    this.onChange('coffee', 150)
  },
  methods: {
    onChange(type, value) {
      const ratio = {
        water: this.ratioWater,
        coffee: this.ratioCoffee,
      }
      this.form[type] = value * ratio[type]
    },
    onChangeRatio(type, value){
      this.base[type] = value
      this.onChange('coffee', this.form.water)
    }
  },
}
</script>

<style scoped></style>
