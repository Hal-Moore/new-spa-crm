<template>
    <main class="content">
    <div class="page-title">
        <h4>Аналитика</h4>
    </div>

    <div class="average-price">
        <p>Средний чек <strong>4 р.</strong></p>
    </div>

    <div class="analytics-block pb3">
        <h5>Выручка</h5>
        <line-chart :chart-data="data" :height="80" :options="{responsive: true}"></line-chart>
    </div>

    <div class="analytics-block">
        <h5>Заказы</h5>
        <line-chart :chart-data="data" :height="80" :options="{responsive: true}"></line-chart>
    </div>

</main>
</template>


<script>
import LineChart from './LineChart.js'
import axios from 'axios';
export default {
  components: {
    LineChart
  },
  data: function(){
    return {
      data: [],
    }
  },
  mounted(){
    this.update()
  },
  methods:{
    update: function() {
      axios.get('/analyt')
      .then((response)=>{
        this.data=response.data
      });
    }
  }
}
</script>

