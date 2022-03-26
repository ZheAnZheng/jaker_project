<template>
  <div>
    <Header />
    <ReserveSection />
    <ServiceSection />
    <ServiceNoSection />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ReserveSection from "./components/ReserveSection.vue";
import ServiceSection from "./components/ServiceSection.vue";
import ServiceNoSection from "./components/ServiceNoSection.vue";

export default {
  name: "App",
  components: {
    Header,
    ReserveSection,
    ServiceSection,
    ServiceNoSection,
  },
};
</script>

<style>
@import "./assets/scss/reset.scss";
@import "./assets/scss/color.scss";
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500&display=swap");
html {
  font-family: "Roboto", sans-serif;
  font-size: 16px;
}
</style>
