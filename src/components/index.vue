<template>
  <div>
    <ul>
      <li v-for="itme in list" :key="itme.name">
        <router-link :to="itme.url">
          {{itme.name}}
        </router-link>

      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Index',
    data() {
      return {
        list: [{name:'认知检查',url:''}, {name:'认知训练',url:'train'}]
      }
    }
  }
</script>

<style>
</style>
