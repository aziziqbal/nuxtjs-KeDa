<template>
  <v-card class="bg">
    <v-card-title>
      <div class="titles">
        KeDA Tech
      </div>
    </v-card-title>

    <v-tabs
      v-model="tab"
      background-color="white"
      color="basil"
      grow
    >
      <v-tab class="tab-title">
        Label
      </v-tab>
      <v-tab class="tab-title">
        Text Field
      </v-tab>
      <v-tab class="tab-title">
        Date Field
      </v-tab>
      <v-tab class="tab-title">
        Select
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <v-tab-item>
        <div class="pd-20">
          <div class="input-group">
            <RadioButton v-for="option in items1" :option="option" :key="option">
              <template slot="label">
                {{ option }}
              </template>
            </RadioButton>
          </div>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          <div class="input-group">
            <RadioButton v-for="(option, index) in items2" :option="option" :key="index"  >
              <template slot="label">
                <input class="input-group2" :value="option">
              </template>
            </RadioButton>
          </div>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          <div class="input-group">
            <RadioButton v-for="(option, index) in items3" :option="option" :key="index"  >
              <template slot="label" >
                  <v-menu
                    ref="menu"
                    v-model="option.menu"
                    :close-on-content-click="false"
                    :return-value.sync="date"
                    transition="scale-transition"
                    offset-y
                    min-width="auto"
                  >
                    <template v-slot:activator="{ on, attrs }">
                      <v-text-field
                        v-model="option.text"
                        readonly
                        v-bind="attrs"
                        v-on="on"
                        outlined
                        dense
                        style="width:200px;"
                        hide-details
                      ></v-text-field>
                    </template>
                    <v-date-picker
                        v-model="option.text"
                      no-title
                      scrollable
                    >
                      <v-spacer></v-spacer>
                      <v-btn
                        text
                        color="primary"
                        @click="option.menu = false"
                      >
                        Cancel
                      </v-btn>
                      <v-btn
                        text
                        color="primary"
                        @click="option.menu = false"
                      >
                        OK
                      </v-btn>
                    </v-date-picker>
                  </v-menu>
              </template>
            </RadioButton>
          </div>
        </div>
      </v-tab-item>

      <v-tab-item>
        <div class="pd-20">
          <div class="input-group">
            <RadioButton v-for="(option, index) in items2" :option="option" :key="index"  >
              <template slot="label">
                <select class="input-select">
                  <option>A</option>
                  <option>B</option>
                  <option>C</option>
                </select>
              </template>
            </RadioButton>
          </div>
        </div>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>
<script>
  export default {
    data () {
      return {
        tab: '',
        items1: ['Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat'],
        items2: ['Januari', 'Februari', 'Maret', 'April', 'Mei', 'Juni'],
        date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        items3: [
          { text: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10), menu: false },
          { text: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10), menu: false },
          { text: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10), menu: false },
        ],
      }
    },
  }
</script>
<style scoped>
.bg {
  background-color: #982e2d;
}
.titles {
  color:white;
  width:100%;
  text-align: center;
  height: 100px;
  font-size:50px;
  padding-top:35px;
}
.tab-title {
  font-family: Montserrat,sans-serif!important;
  text-transform: capitalize;
  font-size:16px;
}
.pd-20 {
  padding:20px;
}
.input-group {
  width: 100%;
  margin: 20px auto;
  padding: 15px 20px;
  border-radius: 8px;
}
.input-group2 {
  width:150px;
  border:1px solid black;
  padding:10px;
  margin-left:10px;
}
.input-select {
  width:150px;
  border:1px solid black;
  padding:10px;
  margin-left:10px;
}
</style>