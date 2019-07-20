<script>
import { Bar, mixins } from 'vue-chartjs'
import axios from '~/plugins/axios'

export default {
  extends: Bar,
  mixins: [mixins.reactiveProp],
  data:() => ({
    sale: [],
    datachart: {
      labels: ["Sales"],
      datasets: [
        {
          label: 'Sales',  
          backgroundColor: '#4c84ff',
          data: []
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false
    },
  }),
    async mounted() {
      await axios.get('sales').then(response=>{
            this.sale = response.data
            for(var i=0;i<this.sale.length; i++) {
              this.datachart.labels[i] = this.sale[i].month
              this.datachart.datasets[0].data[i] = this.sale[i].sales
            }
          })

      this.renderChart(this.datachart, this.options)
  }

}
</script>
