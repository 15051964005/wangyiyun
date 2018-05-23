<template>
  <div class="sglst">
    <nuxt-link class="sgitem" v-for="(item,index) in songs" :to="'/song?id='+item.id" :key="item.id">
      <div class="sgfl">{{(index)<9?('0'+(index+1)):(index+1)}}</div>
      <div class="sgfr">
        <div class="sgchfl">
          <div class="sgtitle">
            {{item.name}}<span>{{item.alia[0]!==undefined?('('+item.alia[0]+')'):''}}</span></div>
          <div class="sginfo"><i class="fa"></i>{{(item.ar.length==1?item.ar[0].name:(item.ar[0].name+' / '+item.ar[1].name))+' - '+item.al.name}}
          </div>
        </div>
        <div class="sgchfr">
          <i class="fa fa-play"></i>
        </div>
      </div>
    </nuxt-link>
  </div>
</template>

<script>

  export default {
    data(){
      return{
        count:0
      }
    },
    props: ['songs'],
    name: "myHotsong"
  }
</script>

<style scoped>

</style>
