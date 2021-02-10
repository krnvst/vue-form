<template>
  <section class="all-forms">
    <ui-select
      :options="inputData.select"
      :default="'go'"
      @input="outputData.select = $event"
    />
    <br>
    <ui-checkbox
      :options="inputData.checkbox"
      v-model="outputData.checkbox"
      @change-checkbox="outputData.checkbox = $event"
    />
    <br>
    <ui-switch
      @click="outputData.switch = !outputData.switch"
      :value="outputData.switch"
    />
    <br>

    <code>
      <p>select: {{ outputData.select }}</p>
      <p>checkbox: {{ outputData.checkbox }}</p>
      <p>switch: {{ outputData.switch }}</p>
    </code>
  </section>
</template>

<script>
import UiSelect from "@/components/UiSelect"
import UiCheckbox from "@/components/UiCheckbox"
import UiSwitch from "@/components/UiSwitch"

export default {
  name: 'AllForms',
  components: {
    UiSelect,
    UiCheckbox,
    UiSwitch,
  },
  data: () => ({
    inputData: {
      select: ['go', 'python', 'rust', 'javascript'],
      checkbox: ['apple', 'orange', 'berry', 'banana'],
    },
    outputData: {
      select: '',
      checkbox: [],
      switch: false,
    }
  })
}
</script>

<style scoped>
.all-forms {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 40px auto;
  max-width: 500px;
  width: 100%
}
</style>
