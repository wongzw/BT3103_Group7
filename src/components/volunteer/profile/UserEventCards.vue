<template>
  <div class="org-card">
    <div class="first-row">
      <div class="first">
        <h2 class="event-title">{{ event.data.eventName }}</h2>
      </div>
    </div>

    <div class="second-row">
      <div class="first">
        <div class="details">
          <img class="image" src="@/assets/calendarIcon.svg" alt="calendar" />
          <h2 class="event-host">{{ event.data.dateStart }}</h2>
        </div>

        <div class="details">
          <img class="image" src="@/assets/clockIcon.svg" alt="clock" />
          <h2 class="event-host">{{ event.data.timeStart }}</h2>
        </div>

        <div class="details">
          <img
            style="width: 29px"
            src="@/assets/locationIcon.svg"
            alt="location"
          />
          <h2 class="event-host">{{ event.data.location }}</h2>
        </div>
      </div>

      <div class="ant-button">
        <a-button
          type="primary"
          size="large"
          class="orange"
          @click="reroute_event"
        >
          View Event</a-button
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserEventCards",
  props: ["event"],
  methods: {
    reroute_event() {
      const route = "/event/" + this.event.id;
      this.$router.push({ path: route });
    },
  },
};
</script>

<style scoped>
.org-card {
  background-color: #fef8f3;
  border-radius: 8px;
  box-shadow: 0px 4px 10px rgba(60, 78, 100, 0.1);
  padding: 21px 32px 24px;
  width: 100%;
  margin-bottom: 2vh;
  border-radius: 5px;
}

.image {
  width: 24px;
}

.details {
  display: flex;
  margin-right: 24px;
}

.first-row,
.second-row,
.first,
.second {
  display: flex;
  justify-content: space-between;
}

.event-title {
  font-family: "Mulish";
  font-weight: 700;
  color: #020957;
}

.event-host {
  color: #020957;
  font-family: "Mulish";
  font-size: 16px;
  font-weight: 700;
  padding-top: 8px;
  margin-left: 12px;
}

.ant-button .orange {
  background-color: #ff5b2e;
  border-color: #ff5b2e;
  border-radius: 5px;
  width: 100%;
  height: auto;
  padding-left: 48px;
  padding-right: 48px;
  white-space: normal;
}

.ant-button .orange:hover {
  /* color: black; */
  background-color: #ff3700;
  border-color: #ff3700;
  transition: 0.3s ease;
}
</style>