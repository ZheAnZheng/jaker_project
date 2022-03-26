<template>
  <div class="service-container">
    <div class="tutorial-container">
      <div class="title">
        <CleanIcon />
        <p>鐘點清潔會掃拿裡?時數怎麼算?</p>
      </div>
      <div class="subtitle">
        可以根據自己的需求查看會清潔的細項，並預估總共需要的時數，當天清潔人員會再討論狀況做些調整！
      </div>
      <Basebutton outline>時數計算教學</Basebutton>
    </div>
    <ServiceGrid />

    <div class="reserving">
      <Basebutton contained> 開始預約> </Basebutton>
    </div>
  </div>
</template>
<script>
import CleanIcon from "./icons/CleanIcon.vue";
import Basebutton from "./UI/BaseButton.vue";
import ServiceGrid from "../components/ServiceGrid.vue";

export default {
  components: {
    CleanIcon,
    Basebutton,
    ServiceGrid,
  },
};
</script>

<style lang="scss" scoped>
.service-container {
  widtd: 100%;
  height: 100%;
  padding: 32px 16px;
  background-color: var(--lightgrey-bg-color);
}
.tutorial-container {
  height: 100%;
  text-align: center;
  .title {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    column-gap: 4px;
    margin-bottom: 8px;
  }
  p {
    font-size: 18px;
    color: var(--text-color);
  }
  .subtitle {
    font-size: 14px;
    color: var(--text-color);

    margin-bottom: 12px;
  }
  button {
    width: 40%;
    margin-bottom: 20px;
  }
}
.reserving {
  margin-top: 32px;
  padding: 0 10%;
}
</style>
