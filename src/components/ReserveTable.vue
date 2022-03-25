<template>
  <div class="table-container">
    <ul class="tabs">
      <li class="active">快速預約</li>
      <li>雙人快清</li>
      <li>指定人員</li>
      <li>定期享優惠</li>
    </ul>
    <div class="table-body">
      <div class="select">
        <LocationIcon />
        <select name="state">
          <option>台北市大同區</option>
        </select>
      </div>
      <div class="select">
        <ClockIcon />
        <select name="state">
          <option>3小時</option>
        </select>
      </div>
      <div class="has-doggy">
        <PetIcon />
        <p>家中有寵物</p>
        <div class="switch">
          <div class="ball" @click="runAnimation">無</div>
        </div>
      </div>
      <BaseButton contained>開始預約，查看清潔價格</BaseButton>
      <div class="table-footer">
        <p>找約過的人員?</p>
        <BaseButton inline>輸入您得手機號碼</BaseButton>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import LocationIcon from "./icons/LocationIcon.vue";
import ClockIcon from "./icons/ClockIcon.vue";
import PetIcon from "./icons/PetIcon.vue";
import BaseButton from "./UI/BaseButton.vue";
export default {
  components: {
    LocationIcon,
    ClockIcon,
    PetIcon,
    BaseButton,
  },
  setup() {
    const isSwitchOn = ref(false);
    return {
      isSwitchOn,
    };
  },
  methods: {
    runAnimation() {
      if (this.isSwitchOn) {
        this.turnOffAnimation();
      } else {
        this.turnOnAnimation();
      }
    },
    turnOnAnimation() {
      this.isSwitchOn = !this.isSwitchOn;
      const ball = document.querySelector(".ball");
      let animate = null;
      let current = 1;
      animate = setInterval(() => {
        if (current < 26) {
          current += 1;
          ball.innerHTML = "";
          ball.style.left = current + "px";
        } else {
          clearInterval(animate);
          ball.innerHTML = "有";
        }
      }, 1);
    },
    turnOffAnimation() {
      this.isSwitchOn = !this.isSwitchOn;
      const ball = document.querySelector(".ball");
      let animate = null;
      let current = 26;
      animate = setInterval(() => {
        if (current > 1) {
          current -= 1;
          ball.innerHTML = "";
          ball.style.left = current + "px";
        } else {
          clearInterval(animate);
          ball.innerHTML = "無";
        }
      }, 1);
    },
  },
};
</script>

<style lang="scss" scoped>
.table-container {
  width: 100%;
  max-width: 460px;
  margin: 33px auto 0 auto;
  .tabs {
    display: flex;
    column-gap: 2px;
  }
  li {
    flex: 1;
    padding: 8px 4px;
    background: var(--lightgrey-bg-color);
    color: var(--dark-mute-color);
    border-radius: 7px 7px 0 0;
    text-align: center;
    font-size: 14px;
    &.active {
      opacity: 0.9;
      background: var(--paper-color);
      color: var(--primary-color);
    }
  }
}
.table-body {
  width: 100%;
  max-width: 460px;

  padding: 30px 35px;
  background: rgba(255, 255, 255, 0.8);
}
.select {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 35px;
  padding: 0 16px;
  margin-bottom: 16px;
  border: 1px solid var(--border-color);
  border-radius: 3px;
  background: var(--paper-color);
  &::after {
    content: "";
    width: 0;
    height: 0;
    border-top: 5px solid var(--mute-color);
    border-right: 4px solid transparent;
    border-bottom: 0px solid;
    border-left: 4px solid transparent;
  }
}
select {
  position: absolute;
  top: 0;
  left: 0;
  appearance: none;
  -moz-appearance: none;
  -webkit-appearance: none;
  -ms-appearance: none;
  width: 100%;
  background: transparent;
  padding: 10px 20%;
  border: unset;
  border-radius: 3px;
}
.has-doggy {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  padding-left: 16px;
  margin-bottom: 12px;
}
$diameter: 32px;
$path: 58px;
.switch {
  position: relative;
  display: flex;
  justify-content: space-around;
  align-items: center;
  color: var(--border-color);
  height: $diameter;
  width: $path;
  border: 1px solid var(--border-color);
  border-radius: $diameter;
  padding: 1px;

  .ball {
    position: absolute;
    top: 1px;
    left: 1px;
    width: $diameter - 4px;
    height: $diameter - 4px;
    border-radius: 50%;
    text-align: center;
    line-height: $diameter - 4px;
    background-color: var(--primary-color);
    color: var(--paper-color);
  }
  &::before {
    content: "無";
  }
  &::after {
    content: "有";
  }
}
.table-footer {
  display: flex;
  margin-top: 9px;
  justify-content: center;
  align-items: center;
  font-size: 12px;
  button {
    font-size: 12px;
  }
}
@media screen and (min-width: 600px) {
  .table-body {
    background-color: var(--paper-color);
  }
}
</style>
