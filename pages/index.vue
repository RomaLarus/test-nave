<template>
<v-layout>
  <v-container class="bg">
    <v-layout>
      <v-flex lg12 md12>
          <h1 class="page-over">Page Overview</h1>
      </v-flex>
    </v-layout>
    <v-layout class="all" v-bind="binding1">
      <v-layout class="top" v-bind="binding2">
        <v-layout class="visitor">
        <v-flex md2 xs12>
          <v-layout>
            <v-flex md2>
              <v-card class="card-visitor" color="#29cb97">
                <v-layout row>
                  <v-flex lg6>
                    <v-icon size="60px" dark class="card-v-content">
                    remove_red_eye
                    </v-icon>
                  </v-flex>
                  <v-flex class="card-v-content" style="margin-left: 25px">
                    <h1 class="card-h">{{informations.visitors}}</h1>
                    <p class="card-p">Visitors</p>
                  </v-flex>
                  <v-flex class="card-v-content">
                  </v-flex>
                </v-layout>
              </v-card>
            </v-flex>
          </v-layout>
        </v-flex>
        </v-layout>
        <v-layout class="users">
        <v-flex md2 xs12>
          <v-layout>
            <v-flex md2>
              <v-card class="card-visitor" color="#fec400">
                <v-layout row>
                  <v-flex lg6>
                    <v-icon size="60px" dark class="card-v-content">
                    group
                    </v-icon>
                  </v-flex>
                  <v-flex class="card-v-content" style="margin-left: 25px">
                    <h1 class="card-h">{{informations.users}}</h1>
                    <p class="card-p">Users</p>
                  </v-flex>
                  <v-flex class="card-v-content">
                  </v-flex>
                </v-layout>
              </v-card>
            </v-flex>
          </v-layout>
        </v-flex>
        </v-layout>
      </v-layout>
      <v-layout class="bottom" v-bind="binding2">
      <v-layout class="sales">
      <v-flex md2 xs12>
          <v-layout>
            <v-flex md2>
              <v-card class="card-visitor" color="#4c84ff">
                <v-layout row>
                  <v-flex lg6>
                    <v-icon size="60px" dark class="card-v-content">
                    attach_money
                    </v-icon>
                  </v-flex>
                  <v-flex class="card-v-content" style="margin-left: 25px">
                    <h1 class="card-h">{{informations.sales}}</h1>
                    <p class="card-p">Sales</p>
                  </v-flex>
                  <v-flex class="card-v-content">
                  </v-flex>
                </v-layout>
              </v-card>
            </v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
      <v-layout class="orders">
        <v-flex md2 xs12>
          <v-layout>
            <v-flex md2>
              <v-card class="card-visitor" color="#ca66ff">
                <v-layout row>
                  <v-flex lg6>
                    <v-icon size="60px" dark class="card-v-content">
                    shopping_cart
                    </v-icon>
                  </v-flex>
                  <v-flex class="card-v-content" style="margin-left: 25px" align>
                    <h1 class="card-h">{{informations.orders}}</h1>
                    <p class="card-p">Orders</p>
                  </v-flex>
                  <v-flex class="card-v-content">
                  </v-flex>
                </v-layout>
              </v-card>
            </v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
      </v-layout>
    </v-layout>
    <v-divider style="margin-bottom: 20px"></v-divider>
    <v-layout v-bind="binding2">
      <v-flex md8 sm3>
        <graph></graph>
      </v-flex>
      <v-flex sm3 class="space"></v-flex>
      <v-flex md4 sm6 class="reportg">
        <reports></reports>
      </v-flex>
      <v-flex md1 class="space"></v-flex>
    </v-layout>
  </v-container>
</v-layout>
</template>

<script>
import axios from "~/plugins/axios"
import Graph from "~/components/Graph"
import Reports from "~/components/Reports"

export default {
    data() {
      return {
        informations: {},
      }
    },
    components: {
      Graph,
      Reports
    },
    mounted() {
      axios.get('informations')
          .then(response => {
            this.informations = response.data
          })
    },
    head() {
      return{
        title: 'Teste Nave'
      }
    },
    computed: {
      binding1() {
        const binding = {}
        binding.column = false
        binding.row = true

        if (this.$vuetify.breakpoint.smAndDown) {
          binding.column = true
          binding.row = false
        }
        return binding
      },
      binding2() {
        const binding = {}
        binding.column = false

        if (this.$vuetify.breakpoint.xs) {
          binding.column = true
        }
        return binding
      },
    }
  }
</script>

<style scoped>
@media only screen and (min-width: 1024px) {
  .reportg {
    padding-top: 15px;
  }
  .space{
    display: none;
  }
  .card-visitor {
    height: 100px;
    width: 229px;
    margin: 10px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
  }
  .card-v-content {
    margin-top: 20px;
    margin-left: 25px;
  }
  .page-over {
    width: 289px;
    height: 37px;
    font-family: Roboto;
    font-size: 34px;
    font-weight: 500;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
    margin-bottom: 25px;
  }
}
@media only screen and (min-width: 426px) and (max-width: 1023px) {
  .space{
    display: block;
  }
  .card-visitor {
    width: 348px;
    height: 100px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    margin-bottom: 20px;
  }
  .page-over {
    width: 289px;
    height: 37px;
    font-family: Roboto;
    font-size: 34px;
    font-weight: 500;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
    margin-bottom: 25px;
  }
  .v-icon {
    margin-left: 20px;
    margin-top: 20px;
  }
  .card-h {
    margin-top: 20px;
  }
}
@media only screen and (max-width: 425px) {
  .space{
    display: block;
  }
  .reportg {
    padding-left: 15px;
  }
  .card-visitor {
    width: 288px;
    height: 100px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    margin-bottom: 20px;
  }
  .page-over {
    width: 289px;
    height: 23px;
    font-family: Roboto;
    font-size: 20px;
    font-weight: 500;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
    margin-bottom: 40px;
  }
  .v-icon {
    margin-left: 20px;
    margin-top: 20px
  }
  .card-h {
    margin-top: 20px;
  }
}
.bg {
  margin: 0;
  max-width: 100%;
  max-height: 100%;
}
.v-divider {
  visibility: hidden;
}
.card-h {
  font-family: Roboto;
  font-size: 28px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #ffffff;
}
.card-p {
  font-family: Roboto;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #ffffff;
  float: right;
}
html {
  background-color: #f4f4f4;
}
.divide {
  visibility: visible;
}
</style>