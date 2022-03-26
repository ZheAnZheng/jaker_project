<template>
  <div class="noservice-container">
    <div class="noservice-title">
      <p>其他未服務內容</p>
      <p>基於人員與客戶安全、隱私等考量</p>
    </div>
    <div class="noservce-content">
      <ul class="box">
        <li v-for="item in boxOne" :key="item.id">
          <CircleIcon small />
          {{ item.description }}
        </li>
      </ul>
      <ul class="box">
        <li v-for="item in boxTwo" :key="item.id">
          <CircleIcon small />
          {{ item.description }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import { v4 } from "uuid";
import CircleIcon from "./icons/CircleIcon.vue";
export default {
  components: {
    CircleIcon,
  },
  setup() {
    const boxOne = ref([
      {
        id: v4(),
        description: "移動或抬起超過10公斤的大型家具或重物",
      },
      {
        id: v4(),
        description: "天花板、高處窗戶及可觸及範圍外的表面清潔",
      },
      {
        id: v4(),
        description: "無危險性外窗清潔及窗簾、紗窗清洗",
      },
      {
        id: v4(),
        description: "寵物排泄及重度汙染區域清潔",
      },
      {
        id: v4(),
        description: "危險化學物質處理",
      },
    ]);
    const boxTwo = ref([
      {
        id: v4(),
        description: "地毯深度清潔及清洗（基本除塵除外）",
      },
      {
        id: v4(),
        description: "各式陳年、染色汙點清潔",
      },
      {
        id: v4(),
        description: "除蟲害（例如：蜂窩、昆蟲…等）",
      },
      {
        id: v4(),
        description: "垃圾清運工作",
      },
      {
        id: v4(),
        description: "室內惡臭環境\n(不指使潔客將已包裝垃圾移至其他地方丟棄）",
      },
      {
        id: v4(),
        description: "車庫清潔（基本掃除除外）園藝或院子清潔。",
      },
    ]);

    return {
      boxOne,
      boxTwo,
    };
  },
};
</script>
<style lang="scss" scoped>
.noservice-container {
  width: 100%;
  height: 100%;
  backgrond-color: var(--paper-color);
  padding: 40px 30px;

  .noservice-title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 22px;
    :nth-child(1) {
      font-size: 18px;
      color: var(--text-color);
    }
    :nth-child(2) {
      font-size: 14px;
      color: var(--important-color);
    }
  }
  .noservce-content {
    display: flex;
    flex-flow: wrap;
    justify-content: space-around;
    .box {
      flex: 0 0 40%;
      min-width: 300px;
    }

    li {
      color: var(--text-color);
      font-size: 14px;
      white-space: pre-wrap;
    }
  }
}
</style>
