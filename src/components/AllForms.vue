<template>
  <div class="all-forms">
    <custom-select
      :options="optionsSelect"
      :default="'go'"
      class="select"
      @input="changeSelect"
    />
    <br>
    <custom-checkbox
      v-model="checkedAnswers"
      :options="optionsCheckbox"
      @change-checkbox="changeCheckbox"
    />
    <br>
    <custom-toggle-switch
      @click="changeSwitch"
      :value="toggleSwitch"
    />
    <br>

    <code>
      <p>selectAnswers: {{ selectAnswers }}</p>
      <p>checkedAnswers: {{ checkedAnswers }}</p>
      <p>toggleSwitch: {{ toggleSwitch }}</p>
    </code>
  </div>
</template>

<script>
import CustomSelect from "./CustomSelect.vue"
import CustomCheckbox from "./CustomCheckbox.vue"
import CustomToggleSwitch from "./CustomToggleSwitch.vue"

export default {
  name: 'AllForms',
  components: {
    CustomSelect,
    CustomCheckbox,
    CustomToggleSwitch,
  },
  data: () => ({
    optionsSelect: ['go', 'python', 'rust', 'javascript'],
    optionsCheckbox: ['apple', 'orange', 'berry', 'banana'],
    toggleSwitch: false,
    selectAnswers: '',
    checkedAnswers: [],
  }),
  methods: {
    changeSelect(value) {
      // console.log('Select ', value)
      this.selectAnswers = value
    },
    changeCheckbox(value) {
      // console.log('Checkbox ', value)
      this.checkedAnswers = value
    },
    changeSwitch() {
      // console.log('Switch ', this.toggleSwitch)
      this.toggleSwitch = !this.toggleSwitch
    }
  }
}
</script>

<style scoped>
.all-forms {
  width: 100%;
}
</style>
