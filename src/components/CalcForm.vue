<template>
  <div class="form">
    <h1 style="padding-bottom: 0.5em;">Калькулятор дат</h1>
    <h2 style="padding-bottom: 0.5em;">Текущая дата {{ currentDate.slice(0,15) }}</h2>
    <div>
      <label for="addDate" id="info">Сколько дней добавить: </label>
      <input 
        v-model="log.addDays"
        type="text" 
        name="addDays" 
        id="addDays"
      >
    </div>
    <button 
      @click="addDate"
    >
      Добавить
    </button>
    <h2 style="padding-top: 0.5em;">Результат: {{ futureDate }}</h2>
  </div>
</template>

<script>
export default {
  name: "CalcForm",
  data() {
    return {
      log: {
        addDays: 0
      },
      futureDate: ''
    }
  },
  props: {
    currentDate: String
  },
  methods: {
    
    addDate() {
      let re = /^-?[0-9]+$/g;
      if(re.test(this.log.addDays)){
        this.futureDate = this.getFutureDate(parseInt(this.log.addDays));
        this.createLog();
      }
      else{
        this.futureDate = 'Введите целое положительно/отрицательное число!'
      }
    },
    getFutureDate(daysAhead) {
      const date = new Date();
      date.setDate(date.getDate() + daysAhead);
      const dateString = date.toString();
      const truncatedString = dateString.slice(0, 15);
      return truncatedString;
    },

    createLog() {
      this.log.currentDate = this.currentDate;
      this.log.futureDate = this.futureDate;
      this.$emit('create', this.log);
      this.log = {
        addDays: ''
      }
    },
  },
}
</script>

<style>
.form {
  padding: 0.5em;
  border: solid teal 0.1em;
  border-radius: 1em;
  box-shadow: 1px 1px 5px 1px gray;
}
</style>