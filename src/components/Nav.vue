<template>
  <nav>
    <router-link to="/money" class="item" active-class="selected animate__headShake">
      <Icon name="money"></Icon>
      记账
    </router-link>
    <router-link to="/labels" class="item" active-class="selected animate__headShake">
      <Icon name="labels"></Icon>
      标签
    </router-link>
    <router-link to="/Statistics" class="item" active-class="selected animate__headShake">
      <Icon name="Statistics"></Icon>
      统计
    </router-link>
  </nav>

</template>

<script>

import "@/assets/icons/labels.svg"
import "@/assets/icons/Statistics.svg"


export default {
  name: "Nav"
}
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.25);
  flex-direction: row;
  font-size: 12px;

  > .item {
    color: darksalmon;
    padding: 2px 0;
    width: 33.33333%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .icon {
      width: 32px;
      height: 32px;
    }

  }
  > .item.selected {
    animation-duration: 800ms; //动画执行时间
    animation-iteration-count: 1; //动画循环次数
    color: coral;
  }

}
</style>