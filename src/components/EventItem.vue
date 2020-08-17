<template>
  <div class="row">
    <div class="col-sm-2">
      <p>{{event.eventType}}</p>
    </div>
    <div class="col-sm-10">
      <h3>{{event.eventDetails}}</h3>
      <h6>{{event.date}}</h6>
      <h6>{{event.time}}</h6>
      <h6>{{event.eventLocation}}</h6>
    </div>
  </div>
</template>
<script>
export default {
  name: "EventItem",
  props: ["event"],
};
</script>
<style scoped>
div {
  text-align: left;
}

.row {
  border: 1px solid #eee;
}
</style>