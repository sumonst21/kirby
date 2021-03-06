<template>
  <div class="k-button-group">
    <slot />
  </div>
</template>

<style>
.k-button-group {
  --button-group-padding-horizontal: .75rem;
  --button-group-padding-vertical: 1rem;
  --button-group-line-height: 1rem;

  font-size: 0;
  margin-left: calc(var(--button-group-padding-horizontal) * -1);
  margin-right: calc(var(--button-group-padding-horizontal) * -1);
}
.k-button-group > .k-dropdown {
  height: calc(var(--button-group-line-height) + (var(--button-group-padding-vertical) * 2));
  display: inline-block;
}
.k-button-group > .k-dropdown > .k-button,
.k-button-group > .k-button {
  padding: var(--button-group-padding-vertical) var(--button-group-padding-horizontal);
  line-height: var(--button-group-line-height);
}
.k-button-group .k-dropdown-content {
  top: calc(100% + 1px);
  margin: 0 var(--button-group-padding-horizontal);
}
</style>
