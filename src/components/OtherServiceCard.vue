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
        <div class="subtitle">非主要清潔內容，但可增加時數請清潔人員執行</div>
        <div v-for="caseItem in item.cases" :key="caseItem.id">
          <div class="case-title">
            <PlusIcon />
            <p>{{ caseItem.title }}</p>
            <p v-if="caseItem.intervalData.max">
              +{{ caseItem.intervalData.min }}~{{ caseItem.intervalData.max }}hr
            </p>
            <p v-else>+{{ caseItem.intervalData.min }}hr</p>
          </div>
          <ServiceItems :service="'include'" :items="caseItem.includes" />
          <ServiceItems :service="'exclude'" :items="caseItem.excludes" />

          <div class="recommend">
            {{ caseItem.recommend }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import ServiceItems from "./UI/ServiceItems.vue";
import PlusIcon from "./icons/PlusIcon.vue";
export default {
  components: {
    ServiceItems,
    PlusIcon,
  },
  props: {
    item: Object,
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
.subtitle {
  font-size: 12px;
  color: var(--mute-color);
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
.case-title {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin-top: 16px;
  font-size: 18px;
  color: var(--text-color);
  column-gap: 8px;
  :nth-child(2) {
    flex: 5;
  }
}
@media screen and (min-width: 600px) {
  .card-content {
    display: flex;
    flex-direction: column;
  }
}
@media screen and (min-width: 600px) {
  .card-content {
    display: flex;
    flex-direction: column;
  }
  .card {
    // height:max-content;
  }
  .drop-toggle {
    display: none;
  }
  .card-body {
    transition: unset;
    opacity: 1;
    height: 100%;
  }
}
</style>
