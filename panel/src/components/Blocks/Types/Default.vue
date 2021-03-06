<template>
  <k-block-title
    :content="content"
    :fieldset="fieldset"
    @dblclick="$emit('open')"
  />
</template>

<style>
.k-block-type-default .k-block-title {
  line-height: 1.5em;
}
</style>
