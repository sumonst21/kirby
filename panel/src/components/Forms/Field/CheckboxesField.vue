<template>
  <k-field
    :counter="counterOptions"
    v-bind="$props"
    class="k-checkboxes-field"
  >
    <k-input
      :id="_uid"
      ref="input"
      v-bind="$props"
      theme="field"
      type="checkboxes"
      v-on="$listeners"
    />
  </k-field>
</template>

<script>
import { props as Input } from "../Input.vue";
import { props as Field } from "../Field.vue";
import { props as CheckboxesInput } from "../Input/CheckboxesInput.vue";
import counter from "@/mixins/forms/counter.js";

export default {
  mixins: [
    Input,
    Field,
    CheckboxesInput,
    counter
  ],
  inheritAttrs: false,
  methods: {
    focus() {
      this.$refs.input.focus();
    }
  }
}
</script>
