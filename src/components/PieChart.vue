<template>
  <div>
    <PieChart :chart-data="datacollection" :options="options" />
  </div>
</template>

<script>
import { Pie } from "vue-chartjs";
import PieChart from "./CreatePieChart.js";

export default {
  extends: Pie,
  components: { PieChart },
  props: ["categorizationData"],
  data() {
    return {
      datacollection: null,
      options: {
        tooltips: {
          callbacks: {
            label: function (tooltipItems, data) {
              const label = data.datasets[0].data;
              const labelText = `${data.labels[tooltipItems.index]}: ${
                label[tooltipItems.index].toLocaleString()
              } 円`;
              return labelText;
            },
          }
        },
      },
    };
  },
  methods: {
    fillData() {
      const pieChartData = this.categorizationData;
      this.datacollection = {
        labels: [
          "住居費",
          "食費",
          "水道光熱費",
          "通信費",
          "お小遣い",
          "預貯金",
          "生命保険料",
          "日用品",
          "医療費",
          "教育費",
          "交通費",
          "被服費",
          "交際費",
          "娯楽費",
          "嗜好品",
          "その他",
        ],
        datasets: [
          {
            backgroundColor: [
              "#FFAD90",
              "#FFABCE",
              "#D0B0FF",
              "#A4C6FF",
              "#A7F1FF",
              "#E9FFA5",
              "#9BF9CC",
              "#AEFFBD",
              "#FF9872",
              "#FF97C2",
              "#C299FF",
              "#8EB8FF",
              "#8EF1FF",
              "#E4FF8D",
              "#86F9C5",
              "#93FFAB",
            ],
            data: [
              pieChartData.rent,
              pieChartData.food,
              pieChartData.utilityBills,
              pieChartData.communication,
              pieChartData.pocketMoney,
              pieChartData.savings,
              pieChartData.lifePremium,
              pieChartData.everydayItems,
              pieChartData.medicalBills,
              pieChartData.education,
              pieChartData.transportation,
              pieChartData.clothing,
              pieChartData.entertainment,
              pieChartData.leisure,
              pieChartData.preference,
              pieChartData.other,
            ],
            borderColor: "#fff",
          },
        ],
      };
    },
  },
};
</script>
