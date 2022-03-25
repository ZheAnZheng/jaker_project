<template>
  <div class="reserve-section-container">
    <div class="bg-img">
      <div class="title">
        <p v-for="item in title" :key="item">{{ item }}</p>
      </div>
      <ReserveTable></ReserveTable>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import ReserveTable from "./ReserveTable.vue";

function changeBgWhenBreakpoint(mobileBg, laptopBg) {
  window.addEventListener("resize", (e) => {
    const img = document.querySelector(".bg-img");
    const widowWidth = e.target.innerWidth;
    if (widowWidth > 600 && img.style.backgroundImage !== mobileBg) {
      img.style.background = `no-repeat top/cover url(${mobileBg})`;
    } else if (widowWidth <= 600 && img.style.backgroundImage !== laptopBg) {
      img.style.background = `no-repeat top/cover url(${laptopBg})`;
    }
  });
}

export default {
  components: {
    ReserveTable,
  },
  setup() {
    const title = ref(["預約居家清潔", "三分鐘馬上搞定!"]);
    const mobileBackground = require("../assets/landing_laptop.png");
    const laptopBackground = require("../assets/landing_mobilebg.png");

    return {
      title: title.value,
      mobileBg: mobileBackground,
      laptopBg: laptopBackground,
    };
  },
  mounted() {
    this.initalBackground(this.mobileBg, this.laptopBg);
    changeBgWhenBreakpoint(this.mobileBg, this.laptopBg);
  },
  methods: {
    initalBackground(mobileBg, laptopBg) {
      const img = document.querySelector(".bg-img");
      if (window.innerWidth > 600) {
        img.style.background = `no-repeat top/cover url(${mobileBg})`;
      } else {
        img.style.background = `no-repeat top/cover url(${laptopBg})`;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.reserve-section-container {
  height: 100%;
  width: 100%;
  padding-top: 50px;

  .bg-img {
    height: 525px;
    width: 100%;
    padding: 20px;
    // background: no-repeat top/cover url("../assets/landing_mobilebg.png");
  }
}
.title {
  margin-top: 60px;
  font-size: 36px;
}

@media screen and (min-width: 600px) {
  .title {
    width: max-content;
    margin-left: auto;
    margin-right: auto;

    p {
      display: inline-block;
      white-space: nowrap;
      &:first-child::after {
        content: ",";
      }
    }
  }
}
</style>
