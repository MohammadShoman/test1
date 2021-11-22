<template>
  <div>
    <input type="date" v-model="startDate" />
    <input type="date" v-model="endDate" />
    <input type="text" v-model="email" />
    <input type="text" @keypress.enter="$fetch" v-model="num" />
    <button @click="getData">click me</button>
    <input type="week" name="week" id="camp-week" v-model="week" required />
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      startDate: "",
      endDate: "",
      num: "",
      email: "",
      week: "",
    };
  },
  async fetch() {
    // this.getData();
  },
  updated() {
    console.log(this.week);
    let week = this.week.split("-")[1].replace(/w/gi, "");
    let year = this.week.split("-")[0];
    console.log(week);
    console.log(this.getDateOfWeek(week, year));
  },
  created() {},
  methods: {
    async getData() {
      console.log(this.num);
      const data = axios.get(
        `http://localhost:5000/appointments/${this.startDate}/${this.endDate}`
      );
      const result = await data;
      this.datas = result;
      console.log("result", this.datas);
    },
    getValue() {
      console.log("email", this.email);
    },
    getDateOfWeek(w, y) {
      var d = 1 + (w - 1) * 7; // 1st of January + 7 days for each week

      return new Date(y, 0, d);
    },
  },
  computed: {},
};
</script>

<style></style>
