<template>
  <div class="digitalCover">
    <div style="width: 50%;position: absolute ;left:25%;bottom: 15%;">
      <!-- <router-link :to="{name:'caption'}"> -->
       <router-link :to="{name:'DigitalCaption'}">
        <div style="width: 50%;float: left;"><img src="@/assets/btnCaption.png" /></div>
      </router-link>
      <div style="width: 50%;float: left;"><img src="@/assets/btnStart.png" @click="$router.push({name:'DigitalReasoning'})"/></div>
    </div>


  </div>
</template>

<script>
  export default{
    methods:{
    },
  }
</script>

<style>
  .digitalCover{
    width: 100%;
    height: 100vh;
    background-image: url(../../../assets/digital4/cover.png);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    /* background-position: center; */
    -moz-background-size: 100% 100%;
  }
</style>
