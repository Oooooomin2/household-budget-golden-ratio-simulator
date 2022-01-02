<template>
  <v-container>
    <v-row>
      <v-col class="mb-4" cols="12" md="6">
        <v-row>
          <v-col cols="12" md="8" lg="6">
            <span v-if="error" class="red--text">{{ error }}</span>
            <v-text-field
              class="font-weight-bold text-h6 mt-4"
              label="月の手取りを入力してください"
              persistent-hint
              outlined
              suffix="円"
              v-model="income"
              @change="calcGoldenRatio"
            ></v-text-field>
            <p>家計の黄金比率は以下になります</p>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" sm="4">
            <v-text-field
              label="住居費"
              suffix="円"
              :value="categorizationData.rent.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="食費"
              suffix="円"
              :value="categorizationData.food.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="水道光熱費"
              suffix="円"
              :value="categorizationData.utilityBills.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="通信費"
              suffix="円"
              :value="categorizationData.communication.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="お小遣い"
              suffix="円"
              :value="categorizationData.pocketMoney.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="預貯金"
              suffix="円"
              :value="categorizationData.savings.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="生命保険料"
              suffix="円"
              :value="categorizationData.lifePremium.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="日用品"
              suffix="円"
              :value="categorizationData.everydayItems.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="医療費"
              suffix="円"
              :value="categorizationData.medicalBills.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="教育費"
              suffix="円"
              :value="categorizationData.education.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="交通費"
              suffix="円"
              :value="categorizationData.transportation.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="被服費"
              suffix="円"
              :value="categorizationData.clothing.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="交際費"
              suffix="円"
              :value="categorizationData.entertainment.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="娯楽費"
              suffix="円"
              :value="categorizationData.leisure.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="嗜好品"
              suffix="円"
              :value="categorizationData.preference.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
          <v-col cols="12" sm="4">
            <v-text-field
              label="その他"
              suffix="円"
              :value="categorizationData.other.toLocaleString()"
              readonly
            ></v-text-field>
          </v-col>
        </v-row>
        <p>
          ※計算結果について、小数点以下は切り捨てで表示しているため、合計金額が一致しないことがございます。
        </p>
      </v-col>
      <v-col offset-md="1" class="mb-4" cols="12" md="5">
        <PieChart
          :categorizationData="categorizationData"
          ref="pieChartMethods"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import PieChart from "./PieChart.vue";

export default {
  components: {
    PieChart,
  },
  data: () => ({
    income: 0,
    error: "",
    categorizationData: {
      rent: 0,
      food: 0,
      utilityBills: 0,
      communication: 0,
      pocketMoney: 0,
      savings: 0,
      lifePremium: 0,
      everydayItems: 0,
      medicalBills: 0,
      education: 0,
      transportation: 0,
      clothing: 0,
      entertainment: 0,
      leisure: 0,
      preference: 0,
      other: 0,
    },
  }),
  methods: {
    calcGoldenRatio() {
      this.error = "";
      const numOnlyRegex = /^[0-9]*$/;
      if (!numOnlyRegex.test(this.income)) {
        this.error = "0以上の半角数値のみを入力してください";
        return false;
      }

      this.categorizationData.rent = Math.floor(this.income * 0.25);
      this.categorizationData.food = Math.floor(this.income * 0.15);
      this.categorizationData.utilityBills = Math.floor(this.income * 0.06);
      this.categorizationData.communication = Math.floor(this.income * 0.05);
      this.categorizationData.pocketMoney = Math.floor(this.income * 0.08);
      this.categorizationData.savings = Math.floor(this.income * 0.18);
      this.categorizationData.lifePremium = Math.floor(this.income * 0.04);
      this.categorizationData.everydayItems = Math.floor(this.income * 0.02);
      this.categorizationData.medicalBills = Math.floor(this.income * 0.01);
      this.categorizationData.education = Math.floor(this.income * 0.04);
      this.categorizationData.transportation = Math.floor(this.income * 0.02);
      this.categorizationData.clothing = Math.floor(this.income * 0.02);
      this.categorizationData.entertainment = Math.floor(this.income * 0.02);
      this.categorizationData.leisure = Math.floor(this.income * 0.02);
      this.categorizationData.preference = Math.floor(this.income * 0.01);
      this.categorizationData.other = Math.floor(this.income * 0.03);

      this.$refs.pieChartMethods.fillData();
    },
  },
};
</script>
