<template>
  <div class="card-container">
    <img class="jaker-avatar" :src="jaker.avatar" />
    <div class="state">{{ jaker.state }}</div>
    <div class="name">{{ jaker.name }}</div>
    <div class="rating">
      <p>{{ jaker.rating }}</p>
      <StarIcon v-for="i in starCount" :key="i"/>
      <HalfStaricon v-show="isHalfStar"/>
    </div>
    <div class="value">${{ jaker.value }}/hr</div>
  </div>
</template>

<script>
import { ref } from "vue";
import StarIcon from "../icons/StarIcon.vue";
import HalfStaricon from "../icons/HalfStarIcon.vue";
export default {
  components: {
    StarIcon,
    HalfStaricon,
  },
  props: {
    jaker: Object,
  },
  setup(props) {
    const { rating } = ref(props.jaker).value;

    const fullStarCount = Math.floor(rating);
    const isHasHalfStar = (rating % 1) * 10 > 4;

    return {
        starCount:fullStarCount,
        isHalfStar:isHasHalfStar
    };
  },
};
</script>

<style lang="scss" scoped>
.card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  min-width: 140px;
  height: 190px;
  background-color: var(--paper-color);
  border-radius: 7px;
  margin: 0 8px;
  color: var(--text-color);
  font-size: 14px;
  .jaker-avatar {
    width: 55px;
    height: 55px;
    border-radius: 50%;
    background-color: var(--mute-color);
  }
  .name {
    color: var(--primary-color);
    font-size: 12px;
  }
  .rating {
    p {
      margin-right: 5px;
    }
    color: var(--mute-color);

    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }
}
</style>
