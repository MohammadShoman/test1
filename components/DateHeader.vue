<template>
  <div>
    <th :key="day" v-for="(day, index) in numberOFday" scope="col">
      {{ addDays(startDate, index).split(" ")[0] }}
      <br />
      {{ addDays(startDate, index).split(" ")[1] }}

      {{ addDays(startDate, index).split(" ")[2] }}
    </th>
  </div>
</template>

<script>
export default {
  name: "DateHeader",
  methods: {
    addDays(date,num) {
      const newD = new Date(date);
      newD.setDate(newD.getDate() + num);
       this.$emit("add-days");
      return newD.toString();
     
    },
  },
watch:{
    dateOfDays(index){
       let one = addDays(this.startDate, index).split(" ")[0];
       let tow = addDays(this.startDate, index).split(" ")[1];
       let three = addDays(this.startDate, index).split(" ")[2];
       return `${one} ${tow} ${three}`
    },
},
  props: {
    startDate: String,
    numberOFday: Number,
  },
};
</script>

<style></style>
