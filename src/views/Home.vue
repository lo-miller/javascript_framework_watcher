<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div>
      <h3>VueJS</h3>
      <p>stars: {{vueData.stargazers_count}} </p>
      <p>watchers: {{vueData.subscribers_count}} </p>
      <p>forks: {{vueData.forks}} </p>
      <h3>AngularJS</h3>
      <p>stars: {{angularData.stargazers_count}} </p>
      <p>watchers: {{angularData.subscribers_count}} </p>
      <p>forks: {{angularData.forks}} </p>
      <h3>Ember</h3>
      <p>stars: {{emberData.stargazers_count}} </p>
      <p>watchers: {{emberData.subscribers_count}} </p>
      <p>forks: {{emberData.forks}} </p>
      <h3>Svelte</h3>
      <p>stars: {{svelteData.stargazers_count}} </p>
      <p>watchers: {{svelteData.subscribers_count}} </p>
      <p>forks: {{svelteData.forks}} </p>
      <h3>React</h3>
      <p>stars: {{reactData.stargazers_count}} </p>
      <p>watchers: {{reactData.subscribers_count}} </p>
      <p>forks: {{reactData.forks}} </p>
    </div>
    <div id="app">
      <div id="chart-container">
        <fusioncharts
        :type="type"
        :width="width"
        :height="height"
        :dataformat="dataFormat"
        :dataSource="dataSource"
        >
        </fusioncharts>
      </div>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
// import Vue from "vue/types/umd";

export default {
  // name: "app",
  data: function () {
    return {
      message: "JavaScript Framework Data",
      vueData: {},
      // vueStars: "",
      angularData: {},
      emberData: {},
      svelteData: {},
      reactData: {},
      type: "column2d",
      renderAt: "chart-container",
      width: "550",
      height: "350",
      dataFormat: "json",
      // dataSource: {
      //   chart: {
      //     caption: "Countries With Most Oil Reserves [2017-18]",
      //     subcaption: "In MMbbl = One Million barrels",
      //     xaxisname: "Country",
      //     yaxisname: "Reserves (MMbbl)",
      //     numbersuffix: "K",
      //     theme: "fusion",
      //   },
      //   data: [
      //     {
      //       label: "VueJS",
      //       value: vueData.stargazers_count,
      //     },
      //     {
      //       label: "Saudi",
      //       value: "260",
      //     },
      //     {
      //       label: "Canada",
      //       value: "180",
      //     },
      //     {
      //       label: "Iran",
      //       value: "140",
      //     },
      //     {
      //       label: "Russia",
      //       value: "115",
      //     },
      //   ],
      // },
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
      console.log(response.data);
      this.vueData = response.data;
      // this.vueStars = response.data.stargazers_count;
    });
    axios
      .get("https://api.github.com/repos/angular/angular.js")
      .then((response) => {
        console.log(response.data);
        this.angularData = response.data;
      });
    axios
      .get("https://api.github.com/repos/emberjs/ember.js")
      .then((response) => {
        console.log(response.data);
        this.emberData = response.data;
      });
    axios
      .get("https://api.github.com/repos/sveltejs/svelte")
      .then((response) => {
        console.log(response.data);
        this.svelteData = response.data;
      });
    axios
      .get("https://api.github.com/repos/facebook/react")
      .then((response) => {
        console.log(response.data);
        this.reactData = response.data;
      });
  },
  methods: {},
};

// const chartData = [
//   {
//     label: "VueJS",
//     value: vueStars,
//   },
//   {
//     label: "Saudi",
//     value: "260",
//   },
//   {
//     label: "Canada",
//     value: "180",
//   },
//   {
//     label: "Iran",
//     value: "140",
//   },
//   {
//     label: "Russia",
//     value: "115",
//   },
// ];
// const dataSource = {
//   chart: {
//     caption: "Countries With Most Oil Reserves [2017-18]",
//     subcaption: "In MMbbl = One Million barrels",
//     xaxisname: "Country",
//     yaxisname: "Reserves (MMbbl)",
//     numbersuffix: "K",
//     theme: "fusion",
//   },
//   data: chartData,
// };
</script>