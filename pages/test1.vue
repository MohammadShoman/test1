<template>
  <div>
    <div class="header">
      <div class="header-itmes"></div>
    </div>

    <div id="calendar-container">
      <div id="calendar" class="first-container" styles>
        <div class="calendar-header">
          <div class="left">
            <h1>CALENDAR</h1>
          </div>
          <div class="filter">
            <label class="container"
              >Doctor
              <input type="radio" checked="checked" name="radio" />
              <span class="checkmark"></span>
            </label>
            <label class="container"
              >Room
              <input type="radio" name="radio" />
              <span class="checkmark"></span>
            </label>
            <label class="container"
              >Procedure
              <input type="radio" name="radio" />
              <span class="checkmark"></span>
            </label>
            <label class="container"
              >Assistant
              <input type="radio" name="radio" />
              <span class="checkmark"></span>
            </label>
          </div>

          <div class="right">
            <div class="button-group">
              <div class="buttons">
                <button type="button" class="weekly-button">Weekly</button>
                <button type="button" class="daily-button">Daily</button>
                <button type="button" class="time-interval-button">
                  Time Interval
                </button>
              </div>
            </div>
          </div>
        </div>
        <div class="calendar-view">
          <table id="calendar">
            <caption>
              August 2014
            </caption>

            <!--  event -->

            <!--  days -->

            <tr class="weekdays">
              <th>&nbsp;</th>
              <th :key="index" v-for="(day, index) in days" scope="col">
                {{ day }}
              </th>
            </tr>

            <tr :key="app.id" class="days" v-for="app in list">
              <th>&nbsp;{{ app.id }}</th>

              <td :key="item" v-for="item in 7" class="day">
                <div v-if="day == app.day" class="event">
                  <div class="event-desc">
                    Career development @ Community College room #402
                  </div>

                  <div class="event-time">2:00pm to 5:00pm</div>
                </div>
              </td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async fetch() {
    await this.getData();
  },
  data() {
    return {
      newValue: "",
      list: [],
      days: ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"],
    };
  },
  methods: {
    async getData() {
      const result = await axios.get(
        `https://619355dcd3ae6d0017da84c7.mockapi.io/doctors`
      );
      this.list = result.data;
      console.log(result.data);
    },
  },
};
</script>

<style>
.container {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 15px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  float: left;
  margin-right: 50px;
  margin-left: 20px;
  font-family: sans-serif;
}
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #eee;
  border-radius: 50%;
}
.container:hover input ~ .checkmark {
  background-color: #ccc;
}
.container input:checked ~ .checkmark {
  background-color: #2196f3;
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
.button-group {
  position: relative;
  display: inline-flex;
  float: right;
}
.buttons {
  margin-right: 20px;
}
.weekly-button {
  font-size: 15px;
  background: #22c8e5;
  border-radius: 20px;
  line-height: 38px;
  padding: 0px 40px;
  border: none;
  color: #fff !important;
  margin-right: 10px;
  font-family: sans-serif;
}
.daily-button {
  font-size: 15px;
  background: #22c8e5;
  border-radius: 20px;
  line-height: 38px;
  padding: 0px 40px;
  border: none;
  color: #fff !important;
  margin-right: 10px;
  font-family: sans-serif;
}
.time-interval-button {
  font-size: 15px;
  background: #22c8e5;
  border-radius: 20px;
  line-height: 38px;
  padding: 0px 35px;
  border: none;
  color: #fff !important;
  font-family: sans-serif;
}
.left {
  font-family: sans-serif;
  font-size: 10px;
  color: burlywood;
}

/* declare a 7 column grid on the table */
#calendar {
  width: 100%;
  grid-template-columns: repeat(7, 1fr);
}

#calendar tr,
#calendar tbody {
  grid-column: 1 / -1;
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  width: 100%;
}

caption {
  text-align: center;
  grid-column: 1 / -1;
  font-size: 130%;
  font-weight: bold;
  padding: 10px 0;
}

#calendar a {
  color: #8e352e;
  text-decoration: none;
}

#calendar td,
#calendar th {
  padding: 5px;
  box-sizing: border-box;
  border: 1px solid #ccc;
}

#calendar .weekdays {
  background: #8e352e;
}

#calendar .weekdays th {
  text-align: center;
  text-transform: uppercase;
  line-height: 20px;
  border: none !important;
  padding: 10px 6px;
  color: #fff;
  font-size: 13px;
}

#calendar td {
  min-height: 180px;
  display: flex;
  flex-direction: column;
}

#calendar .days li:hover {
  background: #d3d3d3;
}

#calendar .date {
  text-align: center;
  margin-bottom: 5px;
  padding: 4px;
  background: #333;
  color: #fff;
  width: 20px;
  border-radius: 50%;
  flex: 0 0 auto;
  align-self: flex-end;
}

#calendar .event {
  flex: 0 0 auto;
  font-size: 13px;
  border-radius: 4px;
  padding: 5px;
  margin-bottom: 5px;
  line-height: 14px;
  background: #e4f2f2;
  border: 1px solid #b5dbdc;
  color: #009aaf;
  text-decoration: none;
}

#calendar .event-desc {
  color: #666;
  margin: 3px 0 7px 0;
  text-decoration: none;
}

#calendar .other-month {
  background: #f5f5f5;
  color: #666;
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
</style>
