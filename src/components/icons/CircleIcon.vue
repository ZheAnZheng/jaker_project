<template>
  <svg
    width="6"
    height="6"
    viewBox="0 0 6 6"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    :class="{ sm: small }"
  >
    <path
      fill-rule="evenodd"
      clip-rule="evenodd"
      d="M3 0C1.34274 0 0 1.34274 0 3C0 4.65726 1.34274 6 3 6C4.65726 6 6 4.65726 6 3C6 1.34274 4.65726 0 3 0Z"
      fill="#3E4459"
    />
    <mask
      id="mask0_2_14782"
      style="mask-type: alpha"
      maskUnits="userSpaceOnUse"
      x="0"
      y="0"
      width="6"
      height="6"
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M3 0C1.34274 0 0 1.34274 0 3C0 4.65726 1.34274 6 3 6C4.65726 6 6 4.65726 6 3C6 1.34274 4.65726 0 3 0Z"
        fill="white"
      />
    </mask>
    <g mask="url(#mask0_2_14782)"></g>
  </svg>
</template>
<script>
export default {
  props: {
    small: Boolean,
  },
};
</script>

<style lang="scss" scoped>
.sm {
  transform: scale(0.5);
}
</style>
