<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<script>
  import { Bar } from "vue-chartjs";
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from "chart.js";

  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

  export default {
    name: "BarChart",
    components: { Bar },
    data() {
      return {
        chartData: {
          labels: ["МТС", "MSBANK", "T"],
          datasets: [
            {
              data: [40, 88, 60],
              backgroundColor: ["#ff6384", "#36a2eb", "#cc65fe"],
            },
          ],
        },
        chartOptions: {
          plugins: {
            legend: {
              display: false,
            },
          },
        },
      };
    },
  };
</script>
