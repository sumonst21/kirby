<template>
  <span
    ref="button"
    :data-size="size"
    class="k-tag"
    tabindex="0"
    @keydown.delete.prevent="remove"
  >
    <span class="k-tag-text"><slot /></span>
    <span v-if="removable" class="k-tag-toggle" @click="remove">&times;</span>
  </span>
</template>

<script>
export default {
  props: {
    removable: Boolean,
    size: String
  },
  methods: {
    remove() {
      if (this.removable) {
        this.$emit("remove");
      }
    },
    focus() {
      this.$refs.button.focus();
    }
  }
};
</script>

<style>
.k-tag {
  position: relative;
  font-size: var(--text-sm);
  line-height: 1;
  cursor: pointer;
  background-color: var(--color-gray-900);
  color: var(--color-light);
  border-radius: var(--rounded-xs);
  display: flex;
  align-items: center;
  justify-content: space-between;
  user-select: none;
}
.k-tag:focus {
  outline: 0;
  background-color: var(--color-focus);
  border-color: var(--color-focus);
  color: #fff;
}
.k-tag-text {
  padding: 0 .75rem;
}
.k-tag-toggle {
  color: rgba(255, 255, 255, .7);
  width: 2rem;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border-left: 1px solid rgba(255, 255, 255, .15);
}
.k-tag-toggle:hover {
  background: rgba(255, 255, 255, .2);
  color: #fff;
}
[data-disabled] .k-tag {
  background-color: var(--color-gray-600);
}
[data-disabled] .k-tag .k-tag-toggle {
  display: none;
}
</style>
