<template>
  <div>
    <InputArea
      ref="inputArea"></InputArea>
    <b-input v-model="spanMonth" style="width:60px; display: inline"></b-input
    >ヵ月分を
    <b-button variant="primary" @click="calc">表示</b-button>
    <hr />
    <div v-show="showResult">
      <div>1ヶ月のincome - expense：{{ resultOne }} 円</div>
      <div>{{　spanMonthResult　}}ヶ月のincome - expense：{{ resultAll }} 円</div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import InputArea from "./InputArea.vue";

@Component({components : { InputArea }})
export default class MainPage extends Vue {
  spanMonth: number = 1;
  spanMonthResult: number = 0;

  resultOne: number = 0;
  resultAll: number = 0;

  showResult: boolean = false;

  calc() {
    let income = this.$refs.inputArea.income;
    let expense = this.$refs.inputArea.expense;
    let periodicExpenses = this.$refs.inputArea.periodicExpenses;

    // 1ヶ月分の計算
    let oneMonthExpense: number = expense;
    periodicExpenses.forEach(periodicExpense => {
      // FIXME parseIntが必要な意味
      oneMonthExpense += parseInt(periodicExpense.expense, 10);
    });
    this.resultOne = income - oneMonthExpense;

    // 全ヶ月分の計算
    let allExpense: number = expense * this.spanMonth;
    periodicExpenses.forEach(periodicExpense => {
      let baseMonth = this.spanMonth;
      if (periodicExpense.month < this.spanMonth) {
        baseMonth = periodicExpense.month;
      }
      allExpense += periodicExpense.expense * baseMonth;
    });
    this.resultAll = (income * this.spanMonth) - allExpense;

    this.spanMonthResult = this.spanMonth;
    this.showResult = true;
  }
}
</script>

<style scoped></style>
