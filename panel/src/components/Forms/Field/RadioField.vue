<template>
  <k-field v-bind="$props" class="k-radio-field">
    <k-input
      :id="_uid"
      ref="input"
      v-bind="$props"
      theme="field"
      type="radio"
      v-on="$listeners"
    />
  </k-field>
</template>

<script>
import { props as Input } from "../Input.vue";
import { props as Field } from "../Field.vue";
import { props as RadioInput } from "../Input/RadioInput.vue";

export default {
  mixins: [
    Input,
    Field,
    RadioInput
  ],  
  inheritAttrs: false,
  methods: {
    focus() {
      this.$refs.input.focus();
    }
  }
}
</script>
