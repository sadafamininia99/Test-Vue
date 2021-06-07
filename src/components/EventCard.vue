<template>
  <div>
    <span class="eyebrows"> @{{ event.time }}on {{ event.date }}</span>
    <h2>{{ event.title }}</h2>
    <h3>{{ event.attendees.lenght }} attendees</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      event: {
        id: 1,
        title: "beach cleanup",
        date: "tues aug 19,2021",
        time: "6:00",
        attendees: [
          {
            id: "abcd124",
            name: "adam sss",
          },
          {
            id: "sadaf",
            name: "amini",
          },
        ],
      },
    };
  },
};
</script>

<style scoped>
h2 {
  color: blue;
}
.eyebrows {
  padding: 12px;
  margin: 30px;
  color: blue;
  text-align: center;
  border: 5px solid #df2f;
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.3), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
}
</style>