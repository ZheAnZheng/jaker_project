<template>
  <button
    :class="{
      contained: contained,
      outline: outline,
      pill: pill,
      inline: inline,
    }"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    contained: Boolean,
    outline: Boolean,
    pill: Boolean,
    inline: Boolean,
  },
};
</script>
<style lang="scss" scoped>
button {
  background: transparent;
  color: var(--primary-color);
  transition: all 0.2s ease-in;
  border-radius: 3px;
  width: 100%;
  padding: 5px 10px;
  font-size: 16px;
  &:hover {
    background: rgba(0, 0, 0, 0.1);
  }
}
.contained {
  background: var(--primary-color);
  color: var(--paper-color);
  border: 1px solid var(--primary-color);
  transition: all 0.2s ease-in;
  &:hover {
    background: transparent;
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
  }
}
.outline {
  background: transparent;
  color: var(--primary-color);
  border: 1px solid var(--primary-color);
  transition: all 0.2s ease-in;
  &:hover {
    background: var(--primary-color);
    color: var(--paper-color);
  }
}
.pill {
  border-radius: 30px;
}
.inline {
  width: unset;
  height: unset;
  padding: 0;
}
</style>
