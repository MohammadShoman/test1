<template>
  <div>
    <h2>A basic HTML table</h2>
<Filterr/>
<ToutalNumberOfCards :numberOfCards="15"/>
<Card color="pink"/>
    <table style="width: 100%">
      <tr>
        <th>Company</th>
        <th>Contact</th>
        <th>Country</th>
      </tr>
      <tr>
        <td>Alfreds Futterkiste</td>
        <td>Maria Anders</td>
        <td>Germany</td>
      </tr>
      <tr>
        <td>Centro comercial Moctezuma</td>
        <td>Francisco Chang</td>
        <td>Mexico</td>
      </tr>
    </table>

    <p>To undestand the example better, we have added borders to the table.</p>
  </div>
</template>

<script>
import Filterr from "../components/Filterr"
import Card from "../components/Card.vue"
import ToutalNumberOfCards from "../components/ToutalNumberOfCards.vue"
export default {
  components:{Filterr,Card,ToutalNumberOfCards},
  
};
</script>

<style>
table,
th,
td {
  border: 1px solid black;
}
</style>
