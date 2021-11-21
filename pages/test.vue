<template>
  <div>
    <input type="date" name="week" required v-model.lazy="startDate" />
    <input type="date" name="week" required v-model.lazy="endDate" />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    {
      return {
        datas: [],
        startDate: "",
        endDate: "",
      };
    }
  },
  async fetch() {
  this.getAppointment();
  },

  methods: {
    async getData() {},
    async getAppointment() {
      const data = axios.get(
        `http://localhost:5000/appointments/${this.startDate}/${this.endDate}`
      );
      const result = await data;
      this.datas = result;
      console.log(result);
    },
  },
};
</script>

<style></style>
