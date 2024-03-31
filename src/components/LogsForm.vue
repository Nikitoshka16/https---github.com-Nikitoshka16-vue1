<template>
  <div>
    <h1>История запросов:</h1>
        <h2 v-if="logs == 0">История запросов пуста!</h2>
        <button v-else @click="clearLogs"> Очистить</button>

        <item-log
            v-for="log in logs"
            :log = "log"
            :key = "log.id"
        >

        </item-log>
  </div>
</template>

<script>

import ItemLog from './ItemLog.vue'

export default {
    components: { ItemLog },
    name: "LogsForm",
    props: {
        logs: {
            type: Array,
            required: true
        }
    },
    methods: {
        clearLogs() {
            this.$emit('clearLogs');
        }
    }
}
</script>

<style scoped>
h1 {
    padding: 0.5em;
}
</style>