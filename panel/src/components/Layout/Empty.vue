<template>
  <component
    :is="element"
    :data-layout="layout"
    :type="element === 'button' ? 'button' : false"
    class="k-empty"
    v-on="$listeners"
  >
    <k-icon
      v-if="icon"
      :type="icon"
    />
    <p><slot /></p>
  </component>
</template>

<script>
export default {
  props: {
    text: String,
    icon: String,
    /**
     * Available options: `list`|`cards`
     */
    layout: {
      type: String,
      default: "list"
    }
  },
  computed: {
    element() {
      return this.$listeners["click"] !== undefined ? "button" : "div";
    }
  }
};
</script>

<style>
/* global styles */
.k-empty {
  display: flex;
  align-items: stretch;
  border-radius: var(--rounded-xs);
  color: var(--color-gray-600);
  border: 1px dashed var(--color-border);
}
button.k-empty {
  width: 100%;
}
button.k-empty:focus {
  outline: none;
}
.k-empty p {
  font-size: var(--text-sm);
  color: var(--color-gray-600);
}
.k-empty > .k-icon {
  color: var(--color-gray-500);
}

/* layout:cards */
.k-empty[data-layout="cards"] {
  text-align: center;
  padding: 1.5rem;
  justify-content: center;
  flex-direction: column;
}
.k-empty[data-layout="cards"] .k-icon {
  margin-bottom: 1rem;
}
.k-empty[data-layout="cards"] .k-icon svg {
  width: 2rem;
  height: 2rem;
}

/* layout:list */
.k-empty[data-layout="list"] {
  min-height: 38px;
}
.k-empty[data-layout="list"] > .k-icon {
  width: 36px;
  min-height: 36px;
  border-right: 1px solid rgba(0, 0, 0, .05);
}
.k-empty[data-layout="list"] > p {
  line-height: 1.25rem;
  padding: .5rem .75rem;
}
</style>
