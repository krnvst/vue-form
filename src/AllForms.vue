<template>
  <section class="all-forms">
    <ui-select
      :options="inputData.select"
      :default="'Выберете вариант..'"
      @input="outputData.select = $event"
    />
    <br>
    <ui-checkbox
      v-model="outputData.checkbox"
      :options="inputData.checkbox"
      @change-checkbox="outputData.checkbox = $event"
    />
    <br>
    <ui-switch
      @click="outputData.switch = !outputData.switch"
      :value="outputData.switch"
    />
    <br>
    <ui-input
      v-model="outputData.input"
      label="Label"
      placeholder="Input"
      type="text"
    />
    <br>
    <ui-textarea
      v-model="outputData.textarea"
      label="Label"
      placeholder="Textarea"
    />
    <br>

    <code>
      <p>select: {{ outputData.select }}</p>
      <p>checkbox: {{ outputData.checkbox }}</p>
      <p>switch: {{ outputData.switch }}</p>
      <p>input: {{ outputData.input }}</p>
      <p>textarea: {{ outputData.textarea }}</p>
    </code>
  </section>
</template>

<script>
import UiSelect from "@/kit/UiSelect"
import UiCheckbox from "@/kit/UiCheckbox"
import UiSwitch from "@/kit/UiSwitch"
import UiInput from "@/kit/UiInput"
import UiTextarea from "@/kit/UiTextarea"

export default {
  name: 'AllForms',
  components: {
    UiSelect,
    UiCheckbox,
    UiSwitch,
    UiInput,
    UiTextarea
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
      input: '',
      textarea: ''
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
