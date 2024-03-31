<template>
  
  <div class="calc">
    <calc-form 
      :currentDate="currentDate"
      @create="createLog"
    />
  </div>
  <div class="logs">
    <logs-form
      :logs = "logs"
      @clearLogs = "clearLogs"
    />
  </div>
</template>

<script>
import CalcForm from '@/components/CalcForm.vue'
import LogsForm from '@/components/LogsForm.vue'

export default {
  name: 'App',
  components: {
    CalcForm,
    LogsForm
  },
  data() {
    return {
      logs: [
        
      ],
      currentDate: Date(),
    }

  },
  methods: {
    createLog(log) {
      this.logs.push(log);
      if(this.logs.length > 10) {
        this.logs.shift();
      }
    },
    clearLogs() {
      this.logs = [];
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 100vh;
}
</style>
