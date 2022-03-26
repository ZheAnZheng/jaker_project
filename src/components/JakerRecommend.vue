<template>
  <div class="recommend-container">
    <div class="box title">
      <p>全台唯一</p>
      <p>挑人員，評價直接看！</p>
    </div>
    <div class="box jaker">
      <JakerCard
        v-for="jaker in recommendJakers"
        :key="jaker.id"
        :jaker="jaker"
      />
    </div>
    <div class="box image">
      <div class="image-group">
        <img src="../assets/picture-one.png" />
        <span> 人員具良民證、 清潔證照</span>
      </div>
      <div class="image-group">
        <img src="../assets/picture-two.png" />
        <span>今天訂明天掃，即時預約超方便</span>
      </div>
      <div class="image-group">
        <img src="../assets/picture-three.png" />
        <span>價錢、履歷、評價 透明公開</span>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import { v4 } from "uuid";
import JakerCard from "./UI/JakerCard.vue";
export default {
  components: {
    JakerCard,
  },
  setup() {
    const recommendJakers = ref([
      {
        id: v4(),
        name: "潔客",
        avatar: require("../assets/jaker-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
      {
        id: v4(),
        name: "刻刻",
        avatar: require("../assets/coco-avatar.png"),
        state: "台北市",
        rating: 4.8,
        value: 500,
      },
      {
        id: v4(),
        name: "啊傑",
        avatar: require("../assets/AJ-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
      {
        id: v4(),
        name: "張碧",
        avatar: require("../assets/BeeChang-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
      {
        id: v4(),
        name: "潔客",
        avatar: require("../assets/jaker-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
      {
        id: v4(),
        name: "刻刻",
        avatar: require("../assets/coco-avatar.png"),
        state: "台北市",
        rating: 4.8,
        value: 500,
      },
      {
        id: v4(),
        name: "啊傑",
        avatar: require("../assets/AJ-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
      {
        id: v4(),
        name: "張碧",
        avatar: require("../assets/BeeChang-avatar.png"),
        state: "台北市",
        rating: 4.7,
        value: 500,
      },
    ]);
    return {
      recommendJakers: recommendJakers,
    };
  },
};
</script>
<style lang="scss" scoped>
.recommend-container {
  height: 100%;
  width: 100%;
  display: gird;
  grid-template-columns: 1fr;
  grid-template-rows: 3fr;
  background-color: var(--lightgrey-bg-color);
}

.box {
  width: 100%;
  height: 100%;
  padding-top: 16px;
  &:nth-of-type(1) {
    grid-area: title;
  }
  &:nth-of-type(2) {
    grid-area: jaker;
  }
  &:nth-of-type(3) {
    grid-area: image;
  }
}
.title {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-color);
}
::-webkit-scrollbar {
  display: none;
}

.jaker {
  overflow: scroll;
  display: flex;
  flex-flow: nowrap;
  cloumn-gap: 5px;
  padding: 14px 0;
}
.card {
  min-width: 140px;
  height: 190px;
  background: var(--paper-color);
  border-radius: 7px;
  margin: 0 10px;
}
.image {
  display: flex;
  flex-direction: column;
  padding: 16px 0;
  width: max-content;
  margin: auto;
  .image-group {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    column-gap: 8px;
    font-size: 14px;
    color: var(--text-color);
  }

  img {
    height: 30px;
    width: 30px;
  }
}

@media screen and (min-width: 600px) {
  .recommend-container {
    display: grid;
    // grid-gap:20px;
    grid-template-columns: 2fr 8fr 9fr 2fr;
    grid-template-rows: 1fr 4fr 4fr 1fr;
    grid-template-areas:
      " . .  . ."
      " . title jaker ."
      " . image jaker ."
      " .  . .  .";
  }
  .title {
    border-bottom: 2px solid var(--text-color);
    border-radius: 2px;
    :nth-child(1) {
      font-size: 72px;
    }
    :nth-child(2) {
      font-size: 36px;
    }
  }
  .image {
    flex-direction: row;
    justify-content: space-around;
    .image-group {
      flex-direction: column;
      flex-basis: 110px;
      text-align: center;
    }
    img {
      height: 110px;
      width: 110px;
    }
  }
  .jaker {
    flex-flow: wrap;
    row-gap: 20px;
  }
}
</style>
