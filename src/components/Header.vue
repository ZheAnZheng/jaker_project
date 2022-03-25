<template>
  <header>
    <img class="logo" src="../assets/jaker_logo.png" />
    <input id="hambuger-toggle" type="checkbox" />
    <label for="hambuger-toggle">
      <div class="hambuger">
        <div class="hambuger-meat"></div>
      </div>
    </label>
    <div class="menu">
      <ul class="navbar">
        <li class="navbar-item">
          <a href="/">
            <HomeIcon />
            <p>找打掃</p>
          </a>
        </li>
        <li class="navbar-item">
          <a href="/">
            <BreifcaseIcon />
            <p>企業清單</p>
          </a>
        </li>
        <li class="navbar-item">
          <div href="/">
            <p class="drop-menu">全部服務</p>
          </div>
        </li>
        <li class="navbar-item">
          <a href="/">
            <p class="primary-color">成為潔客</p>
          </a>
        </li>
        <li class="navbar-item">
          <a href="/">
            <p>生活知識站</p>
          </a>
        </li>
        <li class="navbar-item">
          <BaseButton outline pill> 註冊登入</BaseButton>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
import HomeIcon from "./icons/HomeIcon.vue";
import BreifcaseIcon from "./icons/BriefcaseIcon.vue";
import BaseButton from "./UI/BaseButton.vue";
export default {
  components: {
    HomeIcon,
    BreifcaseIcon,
    BaseButton,
  },
};
</script>

<style lang="scss" scoped>
.primary-color {
  color: var(--primary-color);
}
header {
  position: fixed;
  display: flex;
  z-index: 200;
  height: 51px;
  width: 100%;
  align-items: center;
  justify-content: space-between;
  background: var(--paper-color);
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.1);
  padding-right: 20px;
}
.logo {
  width: 50%;
  object-fit: contain;
}
.hambuger {
  position: relative;
  width: 30px;
  height: 30px;
  border: 2px solid var(--text-color);
  border-radius: 3px;

  .hambuger-meat {
    position: absolute;
    background: var(--text-color);
    border-radius: 2px;
    height: 2px;
    top: 50%;
    left: 5px;
    right: 5px;
    transform: translateY(-50%);
  }
  &::after {
    position: absolute;
    background: var(--text-color);
    border-radius: 2px;
    height: 2px;
    left: 5px;
    right: 5px;
    transform: translateY(-50%);
    content: "";
    top: 75%;
    transition: all 0.2s ease-in;
  }
  &::before {
    position: absolute;
    background: var(--text-color);
    border-radius: 2px;
    height: 2px;
    left: 5px;
    right: 5px;
    transform: translateY(-50%);
    content: "";
    top: 25%;
    transition: all 0.2s ease-in;
  }
}

.menu {
  position: absolute;
  height: 100vh;
  width: 100%;
  top: 100%;
  padding: 0 5%;
  background: var(--paper-color);
  z-index: 250;
  transform: scaleX(0);
  transition: all 0.3s ease-in;
  transform-origin: right;
}
.navbar {
  display: block;
  opacity: 0;
  transition: opacity 0.1s ease-in;
  padding: 15px;
  color: var(--text-color);

  .navbar-item {
    padding: 5% 0;
    a {
      display: flex;
      color: var(--text-color);
      font-weight: 300;
      flex-direction: row;
      align-items: center;
      column-gap: 5px;
    }
  }

  .drop-menu {
    display: block;
    //   width:max-content;
    &::after {
      display: inline-block;
      content: "";
      width: 0;
      height: 0;
      transform: translateY(-50%);
      margin-left: 5px;
      border-top: 5px solid var(--text-color);
      border-right: 4px solid transparent;
      border-bottom: 0px;
      border-left: 4px solid transparent;
    }
  }
}
input[type="checkbox"] {
  display: none;
  &:checked ~ .menu {
    transform: scaleX(1);
    .navbar {
      opacity: 1;
      transition: opacity 0.3s 0.2s ease-in;
    }
  }
  &:checked ~ label {
    .hambuger-meat {
      display: none;
    }
    .hambuger::after {
      top: 50%;
      //1.4為正三角形斜邊比率
      transform: translateY(-50%) rotate(45deg) scaleX(1.4);
    }
    .hambuger::before {
      top: 50%;
      transform: translateY(-50%) rotate(-45deg) scaleX(1.4);
    }
  }
}

@media screen and (min-width: 600px) {
  header {
    padding: 0 10%;
  }
  label[for="hambuger-toggle"] {
    display: none;
  }
  .logo {
    flex: 0 1 15%;
  }
  .menu {
    all: unset;
    position: initial;
    height: 100%;
    width: max-content;
  }
  .navbar {
    all: unset;
    display: flex;
    flex-direaction: row;
    height: 100%;
    align-items: center;
    column-gap: 10px;
  }
  .navbar-item {
    tranform: unset;
    padding: 0 !important;
  }
}
</style>
