<template>
  <div>
    <b-form-group label="income:" label-for="income" label-cols="1">
      <b-form-input v-model="income" id="income"></b-form-input>
    </b-form-group>
    <b-form-group label="expense:" label-for="expense" label-cols="1">
      <b-form-input v-model="expense" id="expense"></b-form-input>
    </b-form-group>
    <b-input v-model="spanMonth" style="width:60px; display: inline"></b-input
    >ヵ月分表示
    <div style="margin-top: 10px"><b-button @click="calc">calc</b-button></div>
    <hr />
    {{ result }} 円
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component({})
export default class MainPage extends Vue {
  income: number = 0;
  expense: number = 0;
  spanMonth: number = 1;

  result: number = 0;

  calc() {
    this.result = (this.income - this.expense) * this.spanMonth;
  }
}
</script>

<style scoped></style>
