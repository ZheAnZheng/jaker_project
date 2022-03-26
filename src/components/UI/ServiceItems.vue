<template>
  <div class="service-container">
    <div v-for="item in items" :key="item.id" class="circle-item">
      <CircleIcon v-if="service === 'include'" />
      <ForkIcon v-else />
      <p>{{ item.title }}</p>
    </div>
  </div>
</template>

<script>
import CircleIcon from "../icons/CircleIcon.vue";
import ForkIcon from "../icons/ForkIcon.vue";
export default {
  components: {
    CircleIcon,
    ForkIcon,
  },
  props: {
    items: Array,
    service: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.service-container {
  margin-top: 12px;
  display: flex;
  flex-direction: row;
  flex-flow: wrap;
  //   column-gap:40px;
  .circle-item {
    flex-basis: 50%;
    margin-bottom: 8px;
    svg {
      height: 10px;
    }
    p {
      margin-left: 8px;
      font-size: 14px;
      display: inline-block;
    }
  }
  .fork-item {
    @extend .circle-item;
    p {
      margin-left: 6px;
    }
  }
}
</style>
