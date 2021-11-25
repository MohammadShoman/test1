<template>
  <div>
    <div class="header">
      <div class="header-items">
        <div class="icon-bar">
          <div class="dropdown">
            <div class="dropdown-content">
              <a href="#">item 1</a>
              <a href="#">item 2</a>
              <a href="#">item 3</a>
            </div>
            <a href="#"
              ><i class="icon"></i
              ><svg
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                aria-hidden="true"
                role="img"
                width="30"
                height="30"
                preserveAspectRatio="xMidYMid meet"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 19.2c-2.5 0-4.71-1.28-6-3.2c.03-2 4-3.1 6-3.1s5.97 1.1 6 3.1a7.232 7.232 0 0 1-6 3.2M12 5a3 3 0 0 1 3 3a3 3 0 0 1-3 3a3 3 0 0 1-3-3a3 3 0 0 1 3-3m0-3A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10c0-5.53-4.5-10-10-10z"
                  fill="#0b5efc"
                /></svg
            ></a>
          </div>

          <h4 class="username">Username</h4>

          <a href="#"
            ><i class="icon"></i
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              aria-hidden="true"
              role="img"
              width="30"
              height="30"
              preserveAspectRatio="xMidYMid meet"
              viewBox="0 0 28 28"
            >
              <g fill="none">
                <path
                  d="M14 3a8.501 8.501 0 0 1 8.497 8.246l.004.255v4.612l1.414 3.644c.038.098.064.201.077.305l.01.158a1.28 1.28 0 0 1-1.15 1.273l-.13.007l-5.22.001a3.502 3.502 0 0 1-6.998.192l-.006-.194l-5.223.001a1.28 1.28 0 0 1-1.235-1.62l.042-.124l1.416-3.644v-4.61A8.501 8.501 0 0 1 14 3zm1.996 18.65L16 21.5l-4.002.002a2.001 2.001 0 0 0 3.998.15zM14 4.5a7.001 7.001 0 0 0-6.997 6.76l-.004.241v4.752a.75.75 0 0 1-.023.184l-.028.088L5.596 20H22.4l-1.348-3.474a.748.748 0 0 1-.045-.18L21 16.254v-4.752A7.001 7.001 0 0 0 14 4.5z"
                  fill="#0b5efc"
                />
              </g></svg
          ></a>
        </div>
      </div>
    </div>

    <div class="calendar-wrapper">
      <div id="calendar-container">
        <div id="calendar1" class="first-container" styles>
          <div class="calendar-header">
            <div class="left"></div>
            <div class="filter">
              <label class="container"
                >Doctor
                <input
                  @change="filterValue('doctors')"
                  type="radio"
                  checked="checked"
                  name="radio"
                />
                <span class="checkmark"></span>
              </label>
              <label class="container"
                >Room
                <input
                  @change="filterValue('rooms')"
                  type="radio"
                  name="radio"
                />
                <span class="checkmark"></span>
              </label>
              <label class="container"
                >Procedure
                <input
                  @change="filterValue('procedures')"
                  type="radio"
                  name="radio"
                />
                <span class="checkmark"></span>
              </label>
              <label change="filterValue('assistants')" class="container"
                >Assistant
                <input
                  @change="filterValue('assistants')"
                  type="radio"
                  name="radio"
                />
                <span class="checkmark"></span>
              </label>
            </div>
            <div class="right">
              <div class="button-group">
                <div class="buttons">
                  <button class="button1">Weekly</button>
                  <button class="button2">Daily</button>
                  <button class="button3">Time Interval</button>
                  <button class="button4">Monthly</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="calendar-view">
        <div class="middle">
          <div class="son">
            <div @click="addValue(-7)" class="arrow1">
              <a
                ><i class="arrow-icon"></i
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  aria-hidden="true"
                  role="img"
                  width="35"
                  height="35"
                  preserveAspectRatio="xMidYMid meet"
                  viewBox="0 0 24 24"
                >
                  <g transform="rotate(180 12 12)">
                    <path
                      fill="#6f9df2"
                      d="M10.46 18a2.23 2.23 0 0 1-.91-.2a1.76 1.76 0 0 1-1.05-1.59V7.79A1.76 1.76 0 0 1 9.55 6.2a2.1 2.1 0 0 1 2.21.26l5.1 4.21a1.7 1.7 0 0 1 0 2.66l-5.1 4.21a2.06 2.06 0 0 1-1.3.46z"
                    />
                  </g></svg
              ></a>
            </div>

            <h2 class="week-from-to">
              {{ startDate.toString().split(" ").slice(1, 4).join(" ") }}
              -
              {{
                addDays(startDate, 7)
                  .toString()
                  .split(" ")
                  .slice(1, 4)
                  .join(" ")
              }}
            </h2>

            <div @click="addValue(7)" class="arrow2">
              <a
                ><i class="arrow-icon-2"></i
                ><svg
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  aria-hidden="true"
                  role="img"
                  width="35"
                  height="35"
                  preserveAspectRatio="xMidYMid meet"
                  viewBox="0 0 24 24"
                >
                  <path
                    fill="#6f9df2"
                    d="M10.46 18a2.23 2.23 0 0 1-.91-.2a1.76 1.76 0 0 1-1.05-1.59V7.79A1.76 1.76 0 0 1 9.55 6.2a2.1 2.1 0 0 1 2.21.26l5.1 4.21a1.7 1.7 0 0 1 0 2.66l-5.1 4.21a2.06 2.06 0 0 1-1.3.46z"
                  /></svg
              ></a>
            </div>
          </div>
        </div>

        <table id="calendar">
          <!--  days -->
          <tr class="weekdays">
            <th>&nbsp;</th>
            <th ref="header" :key="day" v-for="(day, index) in 7" scope="col">
              <br />

              {{ addDays(startDate, index).split(" ")[0] }}
              <br />
              {{ addDays(startDate, index).split(" ")[1] }}

              {{ addDays(startDate, index).split(" ")[2] }}
            </th>

            <th scope="col">
              <div class="arrows2"></div>
            </th>
          </tr>

          <!-- event -->

          <!--  row -->
          <tr :key="index" v-for="(items, index) in list">
            <th>&nbsp; {{ items.name }}</th>

            <td
              :load="console(items.weekDays[index].appointments.length)"
              :key="index"
              v-for="(count, index) in 7"
              class="day"
            >
              <div v-if="items.weekDays[index].appointments.length == 1">
                <div class="event2">
                  <div class="event-desc">
                    {{
                      items.weekDays[index].appointments[0]
                        .appointment_patient_id
                    }}
                  </div>
                  <div class="event-time">
                    {{
                      items.weekDays[index].appointments[0]
                        .appointment_start_time
                    }}
                    to
                    {{
                      items.weekDays[index].appointments[0].appointment_end_time
                    }}
                  </div>
                </div>
              </div>
              <div v-else-if="items.weekDays[index].appointments.length > 1">
                {{ items.weekDays[index].appointments.length }}
              </div>

              <!-- {{
                items.weekDays[index].appointments.length == 1
                  ? "one"
                  : items.weekDays[index].appointments.length > 1
                  ? items.weekDays[index].appointments.length
                  : "0"
              }} -->
              <!-- {{ normalizedList(`${items}`) }}
              {{ property }} -->
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import moment from "moment";
export default {
  created() {
    this.getData();
  },
  methods: {
    filterValue(value) {
      this.filter = value;
      this.getData();
    },

    console(value) {
      console.log(value);
    },
    addValue(value) {
      this.startDate = this.addDays(this.startDate, value);
      this.getData();
    },
    getStratDate(date) {
      var curr = new Date(date); // get current date
      while (curr.getDay() != 6) {
        curr.setDate(curr.getDate() - 1);
      }
      console.log(curr);
      return curr;
    },
    weekFromTo() {
      let from = this.startDate.toString().split(" ").slice(1, 4);
      let to = this.addDays(this.startDate, 7)
        .toString()
        .split(" ")
        .slice(1, 4);

      return `${from}  - ${to}`;
    },

    addDays(date, num) {
      const newD = new Date(date);
      newD.setDate(newD.getDate() + num);
      // const day = newD.toString().split(" ")[0];
      // const month = newD.toString().split(" ")[1];
      // const daydate = newD.toString().split(" ")[2];
      // const fullDate = `${day}
      // ${month}
      //  ${daydate}  `;

      return newD.toString();
    },

    async getData() {
      const result = await axios.get(
        `http://localhost:5000/weeklyAppointments/${this.filter}/'${moment(
          this.startDate
        ).format("YYYY-MM-DD")}'`
      );
      //'2021-11-20'
      this.list = result.data.Users;
      console.log(this.list);
    },
    // getWeekNumber(date) {
    //   let currentdate = new Date(date);
    //   let oneJan = new Date(currentdate.getFullYear(), 0, 1);
    //   let numberOfDays = Math.floor(
    //     (currentdate - oneJan) / (24 * 60 * 60 * 1000)
    //   );
    //   let result = Math.ceil((currentdate.getDay() + 1 + numberOfDays) / 7);
    //   console.log(result);
    //   return result;
    // },
    // onClick(index) {
    //   //console.log(index);
    //   //   return index, this.$refs.header[index].innerHTML;
    //   console.log(this.$refs.header[index].innerHTML);
    // },
  },
  updated() {
    // this.getData();
  },
  data() {
    var self = this;
    return {
      newValue: "",
      list: [],
      filter: "doctors",
      // startDate: this.getStratDate(this.getWeekNumber(new Date()),2021),
      //currentDate: new Date().getDate() - new Date().getDay() ,
      //startDate: this.addDays(new Date(),-4),
      startDate: this.getStratDate(new Date()),
      isMounted: false,
    };
  },
  mounted() {
    this.isMounted = true;
  },
  computed: {
    normalizedList() {
      return (message1) => {
        if (!this.isMounted) {
          return;
        } else {
          let index = Number(message1);
          return this.$refs.header[index].innerHTML;
        }
      };
    },
    property() {
      if (!this.isMounted) {
        return;
      } else {
        this.$refs.header[3].innerHTML;
      }
      // this.$refs is available
    },
  },
};
</script>

<style>
.body {
  margin: 0%;
}
.arrow1 {
  cursor: pointer;
}

.arrow2 {
  cursor: pointer;
}
.header {
  background-color: #c3c0c01c;
  padding: 25px;
}
.header-items {
  margin-right: 2.5%;
  margin-left: 2.5%;
}
.calendar-wrapper {
  padding: 6%;
  background-color: #c3c0c01c;
}
.container {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 13px;
  -ms-user-select: none;
  user-select: none;
  float: left;
  margin-left: 20px;
  font-family: sans-serif;
  margin-bottom: 40px;
}
.container input {
  opacity: 0;
  cursor: pointer;
}
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #fff;
  border-radius: 50%;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.container:hover input ~ .checkmark {
  background-color: #ffffff;
}
.container input:checked ~ .checkmark {
  background-color: #0b5efc;
  box-shadow: 0px 0px 15px 2px rgb(170 167 167 / 25%);
}
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}
.container input:checked ~ .checkmark:after {
  display: block;
}
.container .checkmark:after {
  top: 9px;
  left: 9px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: white;
}
.center {
  padding-top: 25px;
  display: block;
  text-align: center;
  font-size: 20px;
  font-family: sans-serif;
}
.son {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: center;
  flex-wrap: wrap;
}
.button-group {
  position: relative;
  display: inline-flex;
  float: right;
}
.buttons {
  margin-right: 20px;
  font-size: 13px;
}
.button1 {
  background-color: #fff;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.button1:focus {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  cursor: pointer;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.button1:hover {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  border: none;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
  cursor: pointer;
}

.button2 {
  background-color: #fff;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 25px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
}
.button2:focus {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 25px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  cursor: pointer;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.button2:hover {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 25px;
  border: none;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
  cursor: pointer;
}
.button3 {
  background-color: #fff;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 10px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
}
.button3:focus {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 10px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  cursor: pointer;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.button3:hover {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 10px;
  border: none;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
  cursor: pointer;
}
.button4 {
  background-color: #fff;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
}
.button4:focus {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  cursor: pointer;
  text-decoration: none;
  letter-spacing: 1px;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}
.button4:hover {
  background-color: #eceef8;
  border-radius: 5px;
  line-height: 20px;
  padding: 5px 20px;
  border: none;
  color: #0b5efc !important;
  margin-right: 5px;
  font-family: sans-serif;
  border: 1px solid #0b5efc;
  text-decoration: none;
  letter-spacing: 1px;
  cursor: pointer;
}
.filter {
  color: #949191;
}
.left {
  font-family: sans-serif;
  font-size: 10px;
  color: #949191;
  margin-bottom: 20px;
}
.middle {
  padding-top: 50px;
  text-align: center;
  font-size: 17px;
  font-family: sans-serif;
  letter-spacing: 1.8px;
}

#calendar {
  width: 100%;
  grid-template-columns: repeat(7, 12.2%);
  box-shadow: 1px 25px 20px 0px rgb(170 167 167 / 25%);
}
#calendar tr,
#calendar tbody {
  grid-column: 1 / -1;
  display: grid;
  grid-template-columns: repeat(8, 12.5%);
  background-color: #fff;
}
caption {
  text-align: center;
  grid-column: 1 / -1;
  font-size: 130%;
  padding: 10px 0;
  color: #949191;
  font-family: sans-serif;
  letter-spacing: 2px;
}
#calendar a {
  color: #949191;
  text-decoration: none;
}
#calendar td,
#calendar th {
  padding: 5px;
  box-sizing: border-box;
  border: 1px solid #ebe9f1;
}
#calendar .weekdays {
  background: #ffffff;
  border: 1px solid #ebe9f1;
}
#calendar .weekdays th {
  text-align: center;
  border: none !important;
  padding: 10px 6px;
  color: #949191;
  background-color: #fff;
  font-size: 12px;
  font-family: sans-serif;
  font-weight: bold;
  padding: 3px;
}
#calendar td {
  min-height: 130px;
  display: flex;
  flex-direction: column;
}
#calendar .days li:hover {
  background: #d3d3d3;
}

#calendar .event {
  flex: 0 0 auto;
  font-size: 13px;
  border-radius: 4px;
  padding: 5px;
  margin-bottom: 5px;
  line-height: 14px;
  background: #eceef8;
  border: 1px solid #0b5efc;
  color: #0b5efc;
  text-decoration: none;
  margin-top: 40px;
}
#calendar .event-desc {
  color: #949191;
  margin: 3px 0 7px 0;
  text-decoration: none;
  font-size: 80%;
  font-family: sans-serif;
}
#calendar .other-month {
  background: #f5f5f5;
  color: #949191;
}
/* ============================
                  Mobile Responsiveness
     ============================*/
@media (max-width: 768px) {
  #calendar .weekdays,
  #calendar .other-month {
    display: none;
  }
  #calendar li {
    height: auto !important;
    border: 1px solid #ededed;
    width: 100%;
    padding: 10px;
    margin-bottom: -1px;
  }
  #calendar,
  #calendar tr,
  #calendar tbody {
    grid-template-columns: 1fr;
  }
  #calendar tr {
    grid-column: 1 / 2;
  }
  #calendar .date {
    align-self: flex-start;
  }
}
.icon-bar {
  width: 100%;
  background-color: #fff;
  overflow: auto;
  box-shadow: 0px 0px 15px 4px rgb(170 167 167 / 25%);
}
.icon-bar a {
  float: right;
  width: 6%;
  text-align: center;
  padding: 10px 0;
  transition: all 0.3s ease;
  color: white;
  font-size: 25px;
  color: #949191;
  text-decoration: none;
}
.icon2 {
  font-style: inherit;
}
.icon2:hover {
  background-color: #fff;
}

.icon-bar a:hover {
  background-color: #eceef8;
}

.right-bar a:hover {
  background-color: #eceef8;
}

.active {
  background-color: #eceef8;
}
.dropdown-content a:hover {
  background-color: #eceef8;
}

.dropdown:hover .dropdown-content {
  display: inline-grid;
  top: 95px;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #fff;
  min-width: 160px;
  box-shadow: 0px 0px 9px 3px rgb(170 167 167 / 25%);
  z-index: 1;
  right: 78px;
}
.dropdown-content a {
  color: #949191;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  right: 0;
  font-size: 12px;
  font-family: sans-serif;
  width: auto;
}
.arrows {
  float: right;
  margin-left: -20px;
}
.arrows2 {
  float: left;
  margin-left: -20px;
}
#calendar .event2 {
  flex: 0 0 auto;
  font-size: 13px;
  border-radius: 4px;
  padding: 5px;
  margin-bottom: 5px;
  line-height: 14px;
  background: #f8ecf5;
  border: 1px solid #fc0bc8;
  color: #fc0bc8;
  text-decoration: none;
  margin-top: 40px;
}
.username {
  margin-left: 35px;
  float: left;
  font-size: 14px;
  font-family: sans-serif;
  letter-spacing: 3px;
  font-weight: 700;
  color: cornflowerblue;
}
.week-from-to {
  padding-bottom: 5px;
  color: grey;
}
</style>
