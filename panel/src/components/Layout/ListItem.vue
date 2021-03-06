<template>
  <component :is="element" class="k-list-item" v-on="$listeners">
    <k-sort-handle v-if="sortable" />
    <k-link
      :to="link"
      :target="target"
      class="k-list-item-content"
    >
      <span v-if="image" class="k-list-item-image">
        <k-image v-if="imageOptions" v-bind="imageOptions" />
        <k-icon v-else v-bind="icon" />
      </span>
      <span class="k-list-item-text">
        <em>{{ text }}</em>
        <!-- eslint-disable-next-line vue/no-v-html -->
        <small v-if="info" v-html="info" />
      </span>
    </k-link>
    <nav class="k-list-item-options">
      <slot name="options">
        <k-button
          v-if="flag"
          v-bind="flag"
          class="k-list-item-status"
          @click="flag.click"
        />
        <k-status-icon
          v-else-if="statusIcon"
          v-bind="statusIcon"
          class="k-list-item-status"
        />
        <k-button
          v-if="options"
          :tooltip="$t('options')"
          icon="dots"
          alt="Options"
          class="k-list-item-toggle"
          @click.stop="$refs.options.toggle()"
        />
        <k-dropdown-content
          ref="options"
          :options="options"
          align="right"
          @action="$emit('action', $event)"
        />
      </slot>
    </nav>
  </component>
</template>

<script>
import previewThumb from "@/helpers/previewThumb.js";

export default {
  inheritAttrs: false,
  props: {
    element: {
      type: String,
      default: "li"
    },
    image: [Object, Boolean],
    icon: {
      type: Object,
      default() {
        return {
          type: "file",
          back: "black"
        };
      }
    },
    sortable: Boolean,
    text: String,
    target: String,
    info: String,
    link: [String, Function],
    flag: Object,
    options: [Array, Function],
    statusIcon: Object,
  },
  computed: {
    imageOptions() {
      return previewThumb(this.image);
    }
  }
};
</script>

<style>
.k-list-item {
  --list-item-height: 38px;

  position: relative;
  display: flex;
  align-items: center;
  background: var(--color-white);
  border-radius: var(--rounded-xs);
  box-shadow: var(--shadow);
}
[data-disabled] .k-list-item {
  background: var(--color-background);
}
.k-list-item .k-sort-handle {
  position: absolute;
  left: -1.5rem;
  width: 1.5rem;
  height: var(--list-item-height);
  opacity: 0;
}
.k-list:hover .k-sort-handle {
  opacity: .25;
}
.k-list-item:hover .k-sort-handle {
  opacity: 1;
}
.k-list-item.k-sortable-ghost {
  position: relative;
  outline: 2px solid var(--color-focus);
  z-index: 1;
  box-shadow: rgba(17, 17, 17, .25) 0 5px 10px);
}
.k-list-item.k-sortable-fallback {
  opacity: .25 !important;
  overflow: hidden;
}
.k-list-item-image {
  width: var(--list-item-height);
  height: var(--list-item-height);
  overflow: hidden;
  flex-shrink: 0;
  line-height: 0;
}
.k-list-item-image .k-image {
  width: var(--list-item-height);
  height: var(--list-item-height);
  object-fit: contain;
}
.k-list-item-image .k-icon {
  width: var(--list-item-height);
  height: var(--list-item-height);
}
.k-list-item-image .k-icon svg {
  opacity: .5;
}
.k-list-item-content {
  display: flex;
  align-items: center;
  flex-grow: 1;
  flex-shrink: 1;
  overflow: hidden;
  outline: none;
}
.k-list-item-content[data-tabbed] {
  box-shadow: var(--shadow-outline);
}
.k-list-item-text {
  display: flex;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  align-items: baseline;
  width: 100%;
  line-height: 1.25rem;
  padding: .5rem .75rem;
}
.k-list-item-text em {
  font-style: normal;
  margin-right: 1rem;
  flex-grow: 1;
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: var(--text-sm);
  color: var(--color-gray-900);
}
.k-list-item-text small {
  color: var(--color-gray-500);
  font-size: var(--text-xs);
  font-variant-numeric: tabular-nums;
  color: var(--color-gray-600);
  display: none;
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
}
@media screen and (min-width: 30em) {
  .k-list-item-text small {
    display: block;
  }
}
.k-list-item-status {
  height: auto !important;
}
.k-list-item-options {
  position: relative;
  flex-shrink: 0;
}
.k-list-item-options .k-dropdown-content {
  top: var(--list-item-height);
}
.k-list-item-options > .k-button {
  height: var(--list-item-height);
  padding: 0 12px;
}
.k-list-item-options > .k-button > .k-button-icon {
  height: var(--list-item-height);
}
</style>
