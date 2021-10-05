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
      <v-tab class="tab-title">
        Sliders
      </v-tab>
      <v-tab class="tab-title">
        Switches
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab">
      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio1 }}
          <v-radio-group v-model="radio1">
            <radio defaults name="Radio Button 1" value="1" />
            <radio defaults name="Radio Button 2" value="2" />
          </v-radio-group>
        </div>
      </v-tab-item>

      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio2 }}
          <v-radio-group v-model="radio2">
            <radio texts name="Radio Button 1" value="1" />
            <radio texts name="Radio Button 2" value="2" />
          </v-radio-group>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio3 }}
          <v-radio-group v-model="radio3">
            <radio dates />
            <radio dates />
          </v-radio-group>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio4 }}
          <v-radio-group v-model="radio4">
            <radio selects :data="items1"/>
            <radio selects :data="items2"/>
          </v-radio-group>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio5 }}
          <v-radio-group v-model="radio5">
            <radio sliders min="20" max="100" value="30"/>
            <radio sliders min="10" max="80" value="60"/>
          </v-radio-group>
        </div>
      </v-tab-item>
      <v-tab-item>
        <div class="pd-20">
          Selected : {{ radio6 }}
          <v-radio-group v-model="radio6">
            <radio switches :switchvalue="false" />
            <radio switches :switchvalue="true" />
          </v-radio-group>
        </div>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>
<script>
  export default {
    data () {
      return {
        radio1: 1,
        radio2: 1,
        radio3: 1,
        radio4: 1,
        radio5: 1,
        radio6: 1,
        tab: null,
        items1: ['Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat'],
        items2: ['Januari', 'Februari', 'Maret']
      }
    },
  }
</script>
<style scoped>
/* Helper classes */
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
</style>