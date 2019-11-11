<template>
  <b-container>
    <b-row>
      <b-col cols="2">income:</b-col>
      <b-col>
        <b-form-input v-model="income" id="income" style="display:inline-block; width: 90%"></b-form-input>
        <span> 円</span>
      </b-col>
    </b-row>
    <b-row style="margin-top: 24px;">
      <b-col cols="2">expense:</b-col>
      <b-col>
        <b-form-group label="固定支出" label-for="expense">
          <b-form-input v-model="expense" id="expense" style="display:inline-block; width: 90%"></b-form-input>
          <span> 円</span>
        </b-form-group>
        <div style="margin-bottom: 8px">
          <span>定期支出</span>
          <b-button size="sm" @click="addPeriodicExpense">追加</b-button>
        </div>
        <div v-for="(periodicExpense, index) in periodicExpenses"
          :key="index">
          <b-form-input
            v-model="periodicExpense.expense"
            style="display:inline-block; width: 30%"></b-form-input>
          <span> 円</span>
          <span style="margin-left: 12px">満期</span>
          <b-input
            v-model="periodicExpense.month"
            style="width:60px; display: inline"></b-input>
          <span> ヵ月</span>
          <b-button 
            pill
            variant="danger"
            size="sm"
            @click="deletePeriodicExpenseRow(index)">×</b-button>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script lang="ts">
import { Vue, Component, Prop, Emit } from "vue-property-decorator";

@Component({})
export default class InputArea extends Vue {
  // FIXME propsでバインドさせる方法忘れた
  income: number = 30000;
  expense: number = 25000;
  periodicExpenses: Array<{expense: number, month: number}> = [{expense: 1000, month: 1}];

  addPeriodicExpense () {
    this.periodicExpenses.push({expense: 1000, month: 1});
  }

  deletePeriodicExpenseRow (index:number) {
    this.periodicExpenses.splice(index, 1);
  }
}
</script>

<style scoped lang="scss">
.container {
  @media (max-width: 768px) {
    margin: 0;
    padding: 0;
  }
  .row {
    @media (max-width: 768px) {
      display: block;
    }
  }
  .col {
    @media (max-width: 768px) {
      display: block;
    }
  }
}

</style>
