<template>
  <div class="modal" v-if="this.rendered">
    <div class="display">
        <a-avatar :src="this.participantDetails['photoUrl']" :size="78">
          <template #icon><UserOutlined /></template>
        </a-avatar>
      </div>
    <h2>{{ displayFullName }}</h2>

    <div class="details">
      <p>
        Hours Volunteered: {{ this.participantDetails["hoursVolunteered"] }}
      </p>
      <p>No Show Count: {{ this.participantDetails["noShowNum"] }}</p>
      <p>Skills: {{ displaySkills }}</p>
      <p>Badge Awarded: {{ displayBadges }}</p>
      <p>Number of Applied Events: {{ numAppliedEvents }}</p>
      <p>Number of Accepted Events: {{ numAcceptedEvents }}</p>
    </div>
  </div>
</template>

<script>
import { db } from "../../firebase.js";
import { getDoc, doc } from "firebase/firestore";

export default {
  name: "VolunteerProfile",
  props: ["participantId", "participantDetails"],
  mounted() {
    this.rendered = true;
  },
  computed: {
    displaySkills() {
      return this.participantDetails["interests"].join(", ");
    },
    numAppliedEvents() {
      return this.participantDetails["userAppliedEvents"].length;
    },
    numAcceptedEvents() {
      return this.participantDetails["userAcceptedEvents"].length;
    },
    displayFullName() {
        return this.participantDetails["firstName"] + " " + this.participantDetails["lastName"]
    },
    displayBadges() {
      let showBadges = []
      for (let key in this.participantDetails["userBadges"]) {
        showBadges.push(key);
      }
      return showBadges.join(",");
    }
  },
  data() {
    return {
      rendered: false,
    };
  },
};
</script>

<style scoped>
.modal {
  text-align: center;
  color: #020957;
  line-height: 80%;
  flex-direction: column;
}

h2 {
  font-weight: bold;
  color: #020957;
}

.details {
  margin-top: 5%;
}

.display {
  margin-bottom: 5%;
}

p {
  color: #ff5b2e;
  font-weight: bold;
  line-height: 120%;
}
</style>