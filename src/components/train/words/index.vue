<template>
  <div class="wordCover">
    <div style="width: 50%;position: absolute ;left:25%;bottom: 5%;">
      <!-- <router-link :to="{name:'caption'}"> -->
       <router-link :to="{path:'/train/words/caption'}">
        <div style="width: 50%;float: left;"><img src="../../../assets/btnCaption.png" /></div>
      </router-link>
      <div style="width: 50%;float: left;"><img src="../../../assets/btnStart.png" @click="$router.push({name:'WordRecall'})"/></div>
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
  .wordCover{
    width: 100%;
    height: 100%;
    position: fixed;
    background-image: url(../../../assets/words/cover.png);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-position: center;
    -moz-background-size: 100% 100%;
  }
  /* .cover img{
    position: absolute;
    display: inline-block;
    bottom: 10%;
  } */
</style>
