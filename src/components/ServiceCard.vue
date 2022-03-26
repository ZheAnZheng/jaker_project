<template>
  <div class="card">
    <img :src="item.banner" />
    <div class="card-content">
      <div class="card-title">
        {{ item.title }}
      </div>
      <input type="checkbox" :id="item.id" />
      <label class="drop-toggle" :for="item.id"></label>
      <div class="card-body">
        <ServiceItems :service="'include'" :items="item.includes" />
        <ServiceItems :service="'exclude'" :items="item.excludes" />
        <div class="recommend">
          {{ item.recommend }}
        </div>
        <ServiceTimeView
          :intervalData="intervalData"
          :isOneByOne="item.isOneByOne"
        />
        <div v-for="add in item.addition" :key="add.id" class="addition">
          <div class="addition-title">
            <PlusIcon small />
            <p>{{ add.title }}</p>
            <div v-if="add.intervalData.max">
              {{ add.intervalData.min }}hr~{{ add.intervalData.max }}
            </div>
            <div v-else>+ {{ add.intervalData.min }}hr</div>
          </div>
          <div class="addition-content">
            {{ add.description }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import ServiceItems from "./UI/ServiceItems.vue";
import ServiceTimeView from "./UI/ServiceTimeView.vue";

import PlusIcon from "./icons/PlusIcon.vue";
export default {
  components: {
    ServiceItems,
    PlusIcon,
    ServiceTimeView,
  },
  props: {
    item: Object,
  },
  setup() {
    return {
      includes: [
        {
          id: 0,
          title: "Todo",
        },
      ],
      intervalData: {
        min: 0.5,
        max: 1.5,
        minText: "普通清潔",
        maxText: "空間大、許久未整理",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
.card {
  width: 100%;
  height: 100%;
  border-radius: 8px;
  background-color: var(--paper-color);
  overflow: hidden;
}
img {
  width: 100%;
  height: 122px;
  object-fit: cover;
  object-position: top;
  border-radius: 7px 7px 0 0;
}
.card-content {
  padding: 16px 20px;
}
input[type="checkbox"] {
  display: none;
}
.card-title {
  display: inline-block;
}
.drop-toggle {
  display: inline-block;
  position: relative;
  width: 15px;
  height: 15px;
  float: right;
  margin-top: 1.5px;

  &::before {
    content: "";
    display: block;
    position: absolute;
    background-color: var(--mute-color);
    width: 80%;
    height: 2px;
    top: 25%;
    border-radius: 2px;
    transition: transform 0.2s ease-in;
    transform-origin: top left;
    transform: translateY(-50%) rotate(44deg);
  }
  &::after {
    content: "";
    display: block;
    position: absolute;
    background-color: var(--mute-color);
    right: 0;
    width: 80%;
    height: 2px;
    top: 25%;
    border-radius: 2px;
    transform-origin: top right;
    transition: transform 0.2s ease-in;
    transform: translateY(-50%) rotate(-44deg);
  }
}
.card-body {
  height: 0;
  transition: all 0.3s ease-in;
  opacity: 0;
}
input[type="checkbox"]:checked {
  ~ .drop-toggle::after {
    background-color: var(--primary-color);
  }
  ~ .drop-toggle::before {
    background-color: var(--primary-color);
  }
  ~ .card-body {
    height: 100%;
    opacity: 1;
    transform: scaleY(1);
  }
}

.recommend {
  font-size: 12px;
  margin-left: 14px;
  color: var(--mute-color);
}
.addition {
  margin-top: 4px;
  margin-left: auto;
  width: 70%;
  color: var(--mute-color);
  font-size: 12px;
  .addition-title {
    display: flex;
    font-size: 14px;
    color: var(--text-color);
    :nth-child(2) {
      flex: 3 0 50%;
    }
    :nth-child(3) {
      flex: 2 0 20%;
    }
  }
  .addition-content {
    @extend .recommend;
  }
}

@media screen and (min-width: 600px) {
  .card {
    // height:max-content;
  }
  .drop-toggle {
    display: none;
  }
  .card-body {
    transition: unset;
    opacity: 1;
    height: max-content;
  }
}
</style>
