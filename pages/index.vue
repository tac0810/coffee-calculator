<template>
  <el-container>
    <el-col :span="20" :offset="2">
      <el-form :model="form" label-width="120px">
        <el-form-item label="A豆(g)">
          <el-input type='number' v-model.number="form.amountA">
            <template #suffix>g</template>
          </el-input>
        </el-form-item>
        <el-form-item label="B豆(g)">
          <el-input type='number' v-model.number="form.amountB">
            <template #suffix>g</template>
          </el-input>
        </el-form-item>
        <el-form-item label="A豆の比率(%)">
          <el-input type='number' v-model.number="form.ratio">
            <template #suffix>%</template>
          </el-input>
        </el-form-item>
        <el-form-item label="B豆の比率(%)">
          {{ 100 - form.ratio }}%
        </el-form-item>
        <hr>
        <br>
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
  </el-container>
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
  methods: {
    handleChange(value) {
      console.log(value)
    },
  },
}
</script>

<style scoped>
.el-container {
  padding-top: 20px;
  text-align: right;
}
</style>
