<template>
  <v-container fluid>
    <div v-if="defaults">
      <v-radio :value="value">
        <template v-slot:label>
          <div class="ml-2">
            {{ name }}
          </div>
        </template>
      </v-radio>
    </div>
    <div v-if="texts">
      <v-radio :value="value">
        <template v-slot:label>
          <v-text-field
            hide-details
            solo
            dense
            class="ml-2"
            v-model="name"
          ></v-text-field>
        </template>
      </v-radio>
    </div>
    <div v-if="dates">
      <v-radio :value="value">
        <template v-slot:label>
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                readonly
                v-bind="attrs"
                v-on="on"
                outlined
                dense
                hide-details
              ></v-text-field>
            </template>
            <v-date-picker
              v-model="date"
              no-title
              scrollable
            >
              <v-spacer></v-spacer>
              <v-btn
                text
                color="primary"
                @click="menu = false"
              >
                Cancel
              </v-btn>
              <v-btn
                text
                color="primary"
                @click="$refs.menu.save(date)"
              >
                OK
              </v-btn>
            </v-date-picker>
          </v-menu>
        </template>
      </v-radio>
    </div>
    <div v-if="selects">
      <v-radio :value="value">
        <template v-slot:label>
          <v-select
            :items="data"
            :label="name"
            dense
            hide-details
            outlined
          ></v-select>
        </template>
      </v-radio>
    </div>
    <div v-if="sliders">
      <v-radio :value="value">
        <template v-slot:label>
          <v-slider
            :max="max"
            :min="min"
            thumb-label="always"
            v-model="value"
            dense
            hide-details
          ></v-slider>
        </template>
      </v-radio>
    </div>
    <div v-if="switches">
      <v-radio :value="value">
        <template v-slot:label>
          <v-switch
            v-model="switchvalue"
            :label="`${switchvalue.toString()}`"
            dense
          ></v-switch>
        </template>
      </v-radio>
    </div>
  </v-container>
</template>
<script>
export default {
  props: {
    defaults: {
      required: false,
      type: Boolean,
    },
    texts: {
      required: false,
      type: Boolean,
    },
    dates: {
      required: false,
      type: Boolean,
    },
    selects: {
      required: false,
      type: Boolean,
    },
    sliders: {
      required: false,
      type: Boolean,
    },
    switches: {
      required: false,
      type: Boolean,
    },
    name: {
      required: false,
      type: String,
    },
    value: {
      required: false,
      type: String,
    },
    data: {
      required: false,
      type: Array,
    },
    min: {
      required: false,
      type: String,
    },
    max: {
      required: false,
      type: String,
    },
    switchvalue: {
      required: false,
      type: Boolean,
    },
  },
  data() {
    return {
      radioGroup: 1,
      date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
      menu: false,
      modal: false,
      menu2: false,
    };
  },
};
</script>
<style scoped>
.ml-2 {
  margin-left: 10px;
}
</style>
