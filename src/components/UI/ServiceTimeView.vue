<template>
  <div class="time-spend">
    <div class="time-view">
      <TimeIcon />
      <div>
        {{ intervalData.min }}~{{ intervalData.max
        }}<span v-if="isOneByOne">/間</span>
      </div>
    </div>
    <div class="time-slider">
      <div class="context">
        <p>{{ intervalData.minText }}</p>
        <p>{{ intervalData.maxText }}</p>
      </div>
      <div class="line"></div>
      <div class="context">
        <p>{{ intervalData.min }}hr</p>
        <p>{{ intervalData.max }}hr</p>
      </div>
    </div>
  </div>
</template>

<script>
import TimeIcon from "../icons/TimeIcon.vue";
export default {
  components: {
    TimeIcon,
  },
  props: {
    intervalData: {
      type: Object,
      required: true,
    },
    isOneByOne: Boolean,
  },
};
</script>

<style lang="scss" scoped>
.time-spend {
  display: flex;
  justify-content: space-between;
  margin-top: 22px;
  font-size: 14px;
  .time-view {
    flex-basis: 25%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    row-gap: 8px;
  }
  .time-slider {
    flex-basis: 70%;
    font-size: 12px;
    display: flex;
    color: var(--text-color);
    flex-direction: column;
    justify-content: space-between;
  }
  .line {
    width: 100%;
    height: 2px;
    background-color: var(--border-color);
  }
  .context {
    display: flex;
    justify-content: space-between;
  }
}
</style>
