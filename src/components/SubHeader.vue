<template>
  <h4 :class="className">
    <slot></slot>
  </h4>
</template>

<script>
export default {
  name: 'sub-header',
  props: {
    className: [String, Array],
  },
};
</script>

<style scoped>
h4 {
  font-size: 32px;
  font-family: var(--font-secondary), sans-serif;
  color: var(--color-regular-text);
  /* border-bottom: 10px solid var(--color-subheader-text); */
  display: inline-block;
  box-sizing: border-box;
  box-shadow: 0px 10px 0px -1px var(--color-subheader-text);
}

@media (--mobile-narrow) {
  h4 {
    font-size: 24px;
  }
}
</style>
