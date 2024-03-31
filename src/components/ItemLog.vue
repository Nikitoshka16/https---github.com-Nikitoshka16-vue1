<template>
  <div class="item">
    <h3>{{ log.currentDate.slice(0, 15) }} + {{ log.addDays }} = {{ log.futureDate }}</h3>
  </div>
</template>

<script>
export default {
  props: {
    log: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.item {
  display: flex;
  border: 0.1em solid teal;
  border-radius: 0.5em;
  padding: 0.5em;
  align-items: center;
  justify-content: center;
  margin: 0.5em;
  box-shadow: 1px 1px 5px 1px gray;
}

</style>