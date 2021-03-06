<template>
  <div class="k-bar">
    <div v-if="$slots.left" class="k-bar-slot" data-position="left">
      <slot name="left" />
    </div>
    <div v-if="$slots.center" class="k-bar-slot" data-position="center">
      <slot name="center" />
    </div>
    <div v-if="$slots.right" class="k-bar-slot" data-position="right">
      <slot name="right" />
    </div>
  </div>
</template>

<style>
.k-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  line-height: 1;
}
.k-bar-slot {
  flex-grow: 1;
}
.k-bar-slot[data-position="center"] {
  text-align: center;
}
[dir="ltr"] .k-bar-slot[data-position="right"] {
  text-align: right;
}
[dir="rtl"] .k-bar-slot[data-position="right"] {
  text-align: left;
}
</style>
