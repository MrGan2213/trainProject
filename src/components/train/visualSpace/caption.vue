<template>
  <div class="visualSpaceCaption">
    <div v-show="isStep1" style="width: 100%;height: 100%;">
      <img src="@/assets/visualSpace/step1.png" style="width: 100%;height: 100%;" />
      <img src="@/assets/btnPrevDisable.png" style="position: absolute;right: 25%;top:45%;" />
      <img src="@/assets/btnNex.png" style="position: absolute;right: 5%;top:45%;" @click="isStep1=false" />
    </div>
    <div v-show="!isStep1" style="width: 100%;height: 100%;">
      <img src="@/assets/visualSpace/step2.png" style="width: 100%;height: 100%;" />
      <img src="@/assets/btnPrev.png" style="position: absolute;right: 25%;top:45%;" @click="isStep1=true" />
      <img src="@/assets/btnNexDisable.png" style="position: absolute;right: 5%;top:45%;" />
    </div>
    <img src="@/assets/btnStart.png" style="position: absolute;right: 4%;bottom: 5%;" @click="$router.push({name:'VisualSpace'})" />
  </div>
</template>

<script>
  export default {
    data() {
      return {
        isStep1: true,
      }
    }
  }
</script>

<style>
  .visualSpaceCaption {
    overflow-y: hidden;
    width: 100%;
    height: 100%;
    position: absolute;
    background-image: url(../../../assets/visualSpace/captionbg.png);
    background-repeat: no-repeat;
    background-size:cover;
    -moz-background-size: 100% 100%;
  }
</style>
