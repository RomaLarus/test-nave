<template>
    <v-container >
        <v-layout>
            <v-flex lg4>
          <v-form v-model="valid" ref="form">
            <v-container style="padding: 0px">
              <v-card class="card-reports" >
                <v-layout row>
                  <v-flex lg1 sm1>
                  </v-flex>
                  <v-card-title style="padding: 10px;">
                    <v-flex lg12>
                      <h2 class="card-r-h">Reports</h2>
                    </v-flex>
                  </v-card-title>
                </v-layout>
                <v-divider class="divide"></v-divider>
                  <v-list three-line class="lista">
                    <template v-for="(item, index) in report">
                      <v-list-tile :key="index" avatar ripple @click="">
                        <v-list-tile-content>
                          <v-list-tile-avatar>
                            <img :src="item.image">
                          </v-list-tile-avatar>
                          <v-list-tile-title class="text--primary">{{ item.user }}</v-list-tile-title>
                          <v-list-tile-sub-title class="message">{{ item.message }}</v-list-tile-sub-title>
                          <v-list-tile-action-text>{{ item.time }}</v-list-tile-action-text>
                        </v-list-tile-content>
                      </v-list-tile>
                    </template>
                  </v-list>
                  <v-toolbar class="acao" dense>
                    <v-text-field
                    placeholder="Type your comment here..."
                    solo
                    single-line
                    class="txtfld"
                    v-model="message"
                    ></v-text-field>
                    <v-btn flat style="margin-bottom: 15px;">
                      <span class="submit" @click="submit" >Send</span>
                    </v-btn>
                </v-toolbar>
              </v-card>
            </v-container>
          </v-form>
        </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import axios from '~/plugins/axios'

export default {
    data: () => ({
      valid: false,
      message: '',
    }),
    data(){
        return {
            report: [],
        }
    },
    mounted() {
        axios.get('reports')
          .then(response => {
            this.report = response.data
          })
    },
    methods: {
      async submit() {
        await axios.post('reports', {
          user:  "NAVER",
          image: "https://upload.wikimedia.org/wikipedia/commons/7/7c/Profile_avatar_placeholder_large.png",
          message: this.message,
          time: "2 mins ago"
        })
        await axios.get('reports').then(response => {
          this.report = response.data
        })
        this.$refs.form.reset(); 
      }
    }
}
</script>

<style>
@media only screen and (min-width: 1024px) {
  .card-reports {
    width: 312px;
    height: 438px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .card-r-h {
    width: 270px;
    height: 23.1px;
    font-family: Roboto;
    font-size: 16px;
    font-weight: bold;
    font-style: normal;
    font-stretch: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #6c6c6c;
    margin-top: 17px;
    margin-bottom: 3px;
  }
  .acao {
    position: absolute;
    bottom: 0;
    width: 312px;
    height: 40.1px;
    border-radius: 15px;
    box-shadow: 0 -2px 6px 0 rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .lista {
    max-height: 350px; 
    overflow-y: auto;
    overflow-x: hidden;
  }
}
@media only screen and (min-width: 426px) and (max-width: 1023px) {
  .card-reports {
    width: 348px;
    height: 270px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .acao {
    width: 348px;
    height: 40px;
    border-radius: 15px;
    box-shadow: 0 -2px 6px 0 rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .lista {
    max-height: 165px; 
    overflow-y: auto;
    overflow-x: hidden;
  }
}
@media only screen and (max-width: 425px) {
  .card-reports {
    margin-left: -30px;
    width: 288px;
    height: 401px;
    border-radius: 15px;
    box-shadow: 0 0 6px 1px rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .acao {
    width: 288px;
    height: 40px;
    border-radius: 15px;
    box-shadow: 0 -2px 6px 0 rgba(188, 188, 188, 0.5);
    background-color: #ffffff;
  }
  .lista {
    max-height: 350px; 
    overflow-y: auto;
    overflow-x: hidden;
  }
}

::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
::-webkit-scrollbar-thumb {
  background: #888; 
}
::-webkit-scrollbar-thumb:hover {
  background: #555; 
}
.card-r-h {
  width: 270px;
  height: 23.1px;
  font-family: Roboto;
  font-size: 16px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #6c6c6c;
  margin-top: 17px;
  margin-bottom: 3px;
}
.submit {
  width: 31px;
  height: 14px;
  font-family: Roboto;
  font-size: 12px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #4c84ff;
}
.v-text-field.v-text-field--solo:not(.v-text-field--solo-flat) > .v-input__control > .v-input__slot {
  box-shadow: 0 0 0 0;
  padding: 0;
  background-color: inherit;
}
.v-list__tile__title {
    text-align: center;
    position: absolute;
    top: 0;
    margin-top: 10px;
}
.v-list--three-line .v-list__tile {
    height: 120px;
}
.message {
  font-family: Roboto;
  font-size: 12px;
  font-weight: normal;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #6c6c6c;
}
.text--primary {
  font-family: Roboto;
  font-size: 16px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #6c6c6c;
}

</style>
