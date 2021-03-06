<template>
  <div :data-theme="theme" class="k-box" v-on="$listeners">
    <slot>
      <!-- eslint-disable-next-line vue/no-v-html -->
      <k-text v-html="text" />
    </slot>
  </div>
</template>

<script>
export default {
  props: {
    theme: String,
    text: String
  }
};
</script>

<style>
.k-box {
  word-wrap: break-word;
  font-size: var(--text-sm);
}
.k-box:not([data-theme="none"]) {
  background: var(--color-gray-300);
  border-radius: var(--rounded-xs);
  line-height: 1.25rem;
  border-left: 2px solid var(--color-gray-500);
  padding: .5rem 1.5rem;
}
.k-box[data-theme="code"] {
  background: var(--color-gray-900);
  border: 1px solid var(--color-black);
  color: var(--color-light);
  font-family: "Input", "Menlo", monospace;
  font-size: var(--text-sm);
  line-height: 1.5;
}
.k-box[data-theme="button"] {
  padding: 0;
}
.k-box[data-theme="button"] .k-button {
  padding: 0 .75rem;
  height: 2.25rem;
  width: 100%;
  display: flex;
  align-items: center;
  line-height: 2rem;
  text-align: left;
}

.k-box[data-theme="positive"] {
  background: var(--color-green-300);
  border: 0;
  border-left: 2px solid var(--color-positive-light);
  padding: .5rem 1.5rem;
}
.k-box[data-theme="negative"] {
  background: var(--color-red-300);
  border: 0;
  border-left: 2px solid var(--color-negative-light);
  padding: .5rem 1.5rem;
}
.k-box[data-theme="notice"] {
  background: var(--color-orange-300);
  border: 0;
  border-left: 2px solid var(--color-notice-light);
  padding: .5rem 1.5rem;
}
.k-box[data-theme="info"] {
  background: var(--color-focus-300);
  border: 0;
  border-left: 2px solid var(--color-focus-light);
  padding: .5rem 1.5rem;
}

.k-box[data-theme="empty"] {
  text-align: center;
  border-left: 0;
  padding: 3rem 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: var(--color-background);
  color: var(--color-gray-600);
  border: 1px dashed var(--color-border);
}
.k-box[data-theme="empty"] .k-icon {
  margin-bottom: .5rem;
  color: var(--color-gray-500);
}
.k-box[data-theme="empty"] p {
  color: var(--color-gray-600);
}
</style>
