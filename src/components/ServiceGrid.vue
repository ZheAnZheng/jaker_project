<template>
  <div class="grid">
    <ServiceCard v-for="item in serviceItems" :key="item.id" :item="item" />
    <OtherServiceCard :item="otherServiceItem" />
  </div>
</template>
<script>
import { ref } from "vue";
import { v4 } from "uuid";
import ServiceCard from "./ServiceCard.vue";
import OtherServiceCard from "./OtherServiceCard.vue";
export default {
  components: {
    ServiceCard,
    OtherServiceCard,
  },
  setup() {
    const serviceItems = ref([
      {
        id: v4(),
        banner: require("../assets/living-room.png"),
        title: "客廳清潔",
        includes: [
          {
            id: v4(),
            title: "沙發擦拭",
          },
          {
            id: v4(),
            title: "地毯除塵",
          },
          {
            id: v4(),
            title: "桌,櫃擦拭",
          },
          {
            id: v4(),
            title: "地板清潔",
          },
          {
            id: v4(),
            title: "燈具表面擦拭",
          },
          {
            id: v4(),
            title: "雜物整理",
          },
          {
            id: v4(),
            title: "垃圾打包",
          },
        ],
        excludes: [
          {
            id: v4(),
            title: "沙發深層污漬",
          },
          {
            id: v4(),
            title: "地毯深層污漬",
          },
          {
            id: v4(),
            title: "天花板深層污漬",
          },
          {
            id: v4(),
            title: "吊燈清潔",
          },
        ],
        isOneByOne: false,
        recommend: "建議您與潔客可採用安全之方式拆下後，交由潔客做清洗。",
        intervalData: {
          min: 0.5,
          max: 1.5,
          minText: "普通清潔",
          maxText: "空間大,許久未整理",
        },
      },
      {
        id: v4(),
        banner: require("../assets/badroom-bg.png"),
        title: "臥室清潔",
        includes: [
          {
            id: v4(),
            title: "衣櫃外觀擦拭",
          },
          {
            id: v4(),
            title: "桌面清潔",
          },
          {
            id: v4(),
            title: "棉被,衣物整理",
          },
          {
            id: v4(),
            title: "家電外觀擦拭",
          },
          {
            id: v4(),
            title: "地板清潔",
          },
          {
            id: v4(),
            title: "雜物整理",
          },
          {
            id: v4(),
            title: "床單換洗",
          },
          {
            id: v4(),
            title: "垃圾打包",
          },
        ],
        excludes: [
          {
            id: v4(),
            title: "家電拆卸清洗",
          },
          {
            id: v4(),
            title: "整理衣櫃內部衣物",
          },
          {
            id: v4(),
            title: "移動,搬移床鋪",
          },
        ],
        recommend: null,
        isOneByOne: true,
        intervalData: {
          min: 0.5,
          max: 1.5,
          minText: "普通清潔",
          maxText: "空間大,許久未整理",
        },
      },
      {
        id: v4(),
        banner: require("../assets/bathroom-bg.png"),
        title: "浴室清潔",
        includes: [
          {
            id: v4(),
            title: "馬桶刷洗",
          },
          {
            id: v4(),
            title: "鏡面光亮",
          },
          {
            id: v4(),
            title: "浴缸清潔",
          },
          {
            id: v4(),
            title: "磁磚刷洗",
          },
          {
            id: v4(),
            title: "洗手檯面清潔",
          },
          {
            id: v4(),
            title: "浴門清潔",
          },
          {
            id: v4(),
            title: "清理水垢,皂垢",
          },
          {
            id: v4(),
            title: "局部小範圍除霉",
          },
        ],
        excludes: null,
        isOneByOne: true,
        recommend: "建議您與潔客可採用安全之方式拆下後，交由潔客做清洗。",
        intervalData: {
          min: 0.5,
          max: 1.5,
          minText: "普通清潔",
          maxText: "許久未清潔",
        },
        addition: [
          {
            id: v4(),
            title: "全局除霉",
            intervalData: {
              min: 4,
            },
            description:
              "因需用漂白水敷於發霉處3~4小時，因此全區除霉將耗時至少4~8小時(若霉菌已深入內部，有可能無法完全清除乾淨)",
          },
        ],
      },
      {
        id: v4(),
        banner: require("../assets/kichen-bg.png"),
        title: "廚房清潔",
        includes: [
          {
            id: v4(),
            title: "牆面擦拭",
          },
          {
            id: v4(),
            title: "瓦斯爐台",
          },
          {
            id: v4(),
            title: "集油槽油污處理",
          },
          {
            id: v4(),
            title: "抽油煙機",
          },
          {
            id: v4(),
            title: "櫥櫃擦拭",
          },
          {
            id: v4(),
            title: "地板清潔",
          },
          {
            id: v4(),
            title: "冰箱外觀",
          },
          {
            id: v4(),
            title: "洗碗,水槽清潔",
          },
        ],
        excludes: [
          {
            id: v4(),
            title: "廚餘清理",
          },
        ],
        recommend: null,
        isOneByOne: false,
        intervalData: {
          min: 0.5,
          max: 2.5,
          minText: "普通清潔",
          maxText: "油污嚴重,許久未整理",
        },
        addition: [
          {
            id: v4(),
            title: "冰箱內部整理,清潔",
            intervalData: {
              min: 1,
              max: 1.5,
            },
            description: null,
          },
        ],
      },
      {
        id: v4(),
        banner: require("../assets/balcony-bg.png"),
        title: "陽台清潔",
        includes: [
          {
            id: v4(),
            title: "家電外觀擦拭",
          },
          {
            id: v4(),
            title: "水管擦拭",
          },
          {
            id: v4(),
            title: "地板刷洗",
          },
          {
            id: v4(),
            title: "曬衣桿擦拭",
          },
          {
            id: v4(),
            title: "雜物整理",
          },
        ],
        excludes: [
          {
            id: v4(),
            title: "除蟲害",
          },
          {
            id: v4(),
            title: "園藝,花草照料",
          },
        ],
        isOneByOne: false,
        recommend: null,
        intervalData: {
          min: 0.5,
          max: 1.5,
          minText: "普通清潔",
          maxText: "空間大,許久未整理",
        },
      },
    ]);
    const otherServiceItem = ref({
      id: v4(),
      title: "其他清潔",
      banner: require("../assets/other-clean-bg.png"),
      cases: [
        {
          id: v4(),
          title: "窗戶清潔",
          isOneByOne: true,
          intervalData: {
            min: 0.5,
          },
          includes: [
            {
              id: v4(),
              title: "內側,底溝擦拭",
            },
            {
              id: v4(),
              title: "玻璃窗內部清洗",
            },
            {
              id: v4(),
              title: "紗窗內部清潔",
            },
          ],
          excludes: [
            {
              id: v4(),
              title: "拆卸窗戶清洗",
            },
            {
              id: v4(),
              title: "拆窗戶,清洗",
            },
          ],
          recommend:
            "以安全為前提下，『兩位』服務人員以上才提供拆洗窗戶、紗窗的服務，或者您可以自行拆下，再由服務人員做清洗",
        },
        {
          id: v4(),
          isOneByOne: false,
          title: "衣物洗曬",
          intervalData: {
            min: 1,
            max: 2,
          },
          includes: [
            {
              id: v4(),
              title: "衣物清洗",
            },
            {
              id: v4(),
              title: "衣物晾曬",
            },
            {
              id: v4(),
              title: "需備有洗衣機",
            },
          ],
          excludes: [
            {
              id: v4(),
              title: "特殊清洗衣物(乾洗)",
            },
            {
              id: v4(),
              title: "手洗衣物",
            },
            {
              id: v4(),
              title: "整燙衣服",
            },
          ],
          recommend: null,
        },
      ],
    });
    return {
      serviceItems,
      otherServiceItem,
    };
  },
};
</script>
<style lang="scss" scoped>
.grid {
  height: 100%;
  display: grid;
  grid-template-columns: 1fr;
  grid-auto-rows: auto;
  row-gap: 20px;
  column-gap: 20px;
}
.grid-item {
  width: 100%;
  height: 174px;
  background: rgba(0, 0, 255, 0.3);
  border: 1px solid rgba(0, 0, 0, 0.1);
}
@media screen and (min-width: 600px) {
  .grid {
    width: 90%;
    margin: 0 auto;
    grid-template-columns: 1fr 1fr 1fr;
    grid-auto-rows: 6fr 1fr 8fr;
    grid-template-areas:
      "living kitchen balcony"
      "living kitchen other"
      "bathroom bedroom other";
    :nth-child(1) {
      grid-area: living;
    }
    :nth-child(2) {
      grid-area: bedroom;
    }
    :nth-child(3) {
      grid-area: bathroom;
    }
    :nth-child(4) {
      grid-area: kitchen;
    }
    :nth-child(5) {
      grid-area: balcony;
    }
    :nth-child(6) {
      grid-area: other;
    }
  }
}
</style>
