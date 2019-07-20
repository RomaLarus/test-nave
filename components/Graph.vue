<template>
    <v-container class="cc">
        <v-layout>
          <v-card class="card-graph">
            <v-layout row>
              <v-flex lg12>
                <v-card-title>
                  <h2 class="card-g-h">Site Traffic Overview</h2>
                </v-card-title>
              </v-flex>
            </v-layout>
            <v-card-text class="card-text">
              <sales class="sales"/>
            </v-card-text>
          </v-card>
      </v-layout>
    </v-container>
</template>

<script>
import axios from '~/plugins/axios'
import Sales from '~/components/Sales'

export default {
    components: {
      Sales
    },   
}
</script>

<style scoped>
@media only screen and (min-width: 1024px) {
  .card-graph {
    width: 644px;
    height: 438px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
    margin-top: 15px;
  }
  .sales {
    max-height: 330px;
  }
  .card-g-h {
    width: 270px;
    height: 23px;
    font-family: Roboto;
    font-size: 16px;
    font-weight: bold;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
    margin-top: 17px;
    margin-left: 15px;
  }
  .card-text {
    max-height: 350px; 
    overflow: hidden;
  }
}
@media only screen and (min-width: 426px) and (max-width: 1023px) {
  .card-graph {
    width: 348px;
    height: 270px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .sales {
    max-height: 200px;
  }
  .card-g-h {
    width: 270px;
    height: 23px;
    font-family: Roboto;
    font-size: 16px;
    font-weight: bold;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
  }
}
@media only screen and (max-width: 425px) {
  .cc {
    margin-left: -15px;
  }
  .card-graph {
    width: 288px;
    height: 250px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .card-g-h {
    width: 270px;
    height: 23px;
    font-family: Roboto;
    font-size: 16px;
    font-weight: bold;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
  }
  .sales {
    max-height: 200px;
  }
}
p {
  font-weight: bolder;
}
</style>

