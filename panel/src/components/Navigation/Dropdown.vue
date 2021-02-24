<template>
  <span class="k-dropdown" @click.stop>
    <slot />
  </span>
</template>

<script>
/**
 * Dropdowns always consist of a wrapping `k-dropdown` element and the `k-dropdown-content` element. The wrapper is used for positioning, so the dropdown will open relatively to the button or any other element that serves as the toggle. The dropdown content can contain any number of `k-dropdown-item` elements or any other HTML
 */
export default {}
</script>

<style lang="scss">
.k-dropdown {
  position: relative;
}
</style>
