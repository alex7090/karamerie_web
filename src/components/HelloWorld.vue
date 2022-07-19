<template>
  <div class="hello">
    <h1>La Karamerie arrive bientôt</h1>

    <Countdown
      class="timer"
      :deadlineDate="data"
      :mainColor="'#ffffff'"
      :labels="labels"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import { CronJob } from "cron";
//@ts-ignore
import { Countdown } from "vue3-flip-countdown";

export default defineComponent({
  name: "HelloWorld",
  components: {
    Countdown,
  },
  data() {
    return {
      data: new Date(1659121200000),
      aim: "1659121200",
      aim_ms: "1659121200000",
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      daysD: "0",
      hoursD: "0",
      minutesD: "0",
      secondsD: "0",
      labels: {
        days: "Jours",
        hours: "Heures",
        minutes: "Minutes",
        seconds: "Secondes",
      },
    };
  },
  async created() {
    var job = new CronJob(
      "* * * * * *",
      () => {
        const real = new Date().getTime();
        var difference = 1659128400000 - real;

        this.days = Math.floor(difference / 1000 / 60 / 60 / 24);
        difference -= this.days * 1000 * 60 * 60 * 24;

        this.hours = Math.floor(difference / 1000 / 60 / 60);
        difference -= this.hours * 1000 * 60 * 60;

        this.minutes = Math.floor(difference / 1000 / 60);
        difference -= this.minutes * 1000 * 60;

        this.seconds = Math.floor(difference / 1000);
        this.daysD = this.days.toString().padStart(2, "0");
        this.hoursD = this.hours.toString().padStart(2, "0");
        this.minutesD = this.minutes.toString().padStart(2, "0");
        this.secondsD = this.seconds.toString().padStart(2, "0");
      },
      null,
      true,
      "America/Los_Angeles"
    );

    const followedAt = new Date("2023-12-25T15:49:57Z");
    const currentDate = new Date();
    const diffTime = Math.abs(followedAt.getTime() - currentDate.getTime());
    const diffTotalHours = Math.floor(diffTime / (1000 * 60 * 60));
    const diffDays = Math.floor(diffTotalHours / 24);
    const diffHoursWithoutDays = diffTotalHours % 24;

    console.log(`${diffDays} days and ${diffHoursWithoutDays} hours`);
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.flip-clock__slot {
  margin-top: 5px;
}
.timer {
  padding-top: 20px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
