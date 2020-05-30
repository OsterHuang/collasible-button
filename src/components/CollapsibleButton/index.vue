<template>
  <div ref="container" class="collapsible-button" @click="onToggle">
    <div class="icon-img" :class="{ expanded: isExpanded }">&lt;</div>
    <SampleButton1 class="inner-item" />
    <SampleButton1 class="inner-item" />
    <SampleButton1 class="inner-item" />
    <SampleButton1 v-for="x in 5" :key="x" class="inner-item" />
  </div>
</template>

<script>
import SampleButton1 from "./SampleButton1";

export default {
  components: {
    SampleButton1
  },
  data() {
    return {
      isExpanded: false
    };
  },
  mounted() {
    this.translateItems();
  },
  watch: {
    isExpanded() {
      this.translateItems();
    }
  },
  methods: {
    onToggle() {
      this.isExpanded = !this.isExpanded;
    },
    translateItems() {
      const baseBottom = 44;
      this.$refs.container.children.forEach((el, idx) => {
        if (!el.className.includes("inner-item")) return;
        el.style.bottom = baseBottom + (this.isExpanded ? idx * 40 : 0) + "px";
        el.style.opacity = this.isExpanded ? 1 : 0;
      });
    }
  }
};
</script>

<style lang="stylus" scoped>
.collapsible-button
  position fixed
  bottom 40px
  right 20px
  z-index 7

  user-select none

  > .icon-img
    display flex
    align-items center
    justify-content center

    width 40px
    height 40px
    border 1px solid #777
    border-radius 20px
    background-color #ccc

    transition transform 0.3s ease-out
    transition-delay 0.3s
    transform rotate(90deg)
    &.expanded
      transform rotate(270deg)

  .inner-item
    position fixed
    right 22px
    z-index -1
    transition all 0.5s
    opacity 0
</style>
