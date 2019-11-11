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
    <div v-show="showResult">
      1ヶ月：{{ resultOne }} 円
      {{spanMonth}}ヶ月：{{ resultAll }} 円
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component({})
export default class MainPage extends Vue {
  income: number = 30000;
  expense: number = 10000;
  spanMonth: number = 1;

  resultOne: number = 0;
  resultAll: number = 0;

  showResult: boolean = false;

  calc() {
    this.resultOne = this.income - this.expense;
    this.resultAll = this.resultOne * this.spanMonth;
    this.showResult = true;
  }
}
</script>

<style scoped></style>
