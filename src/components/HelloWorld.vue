<template>
  <section class="section">
    <div class="container">
      <h1 class="title">
        Hello World
      </h1>
      <p class="subtitle">
        My first website with <strong>Bulma</strong>!
      </p>
      <div class="columns">
        <div class="column">
          <canvas id="planet-chart" height="100px"></canvas>
        </div>
        <div class="column">
          <ul>
            <li v-for="(item,index) in items" v-bind:key="index"> {{item.message}} <input type="number" placeholder="1.00" step="0.01" min="0" max="100" v-model="items[index].message"></li>
          </ul>
          <input type="number" v-model="planetChartData.data.datasets[1].data[0]">
          <button class="button" v-on:click="createChart('planet-chart', planetChartData)">Update Model </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Chart from 'chart.js'
import planetChartData from './chart-data.js';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    createChart(chartId, chartData) {
      const ctx = document.getElementById(chartId);
      const myChart = new Chart(ctx, {
        type: chartData.type,
        data: chartData.data,
        options: chartData.options,
      });
      console.log(myChart);
    }
  },
  data() {
    return {
      planetChartData: planetChartData,
      items: [{message: 'm1'}, {message: 'm2'}]
    }
  },
  mounted() {
    this.createChart('planet-chart', this.planetChartData);
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
