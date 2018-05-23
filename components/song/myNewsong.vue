<template>
  <div class="sglst">
    <nuxt-link class="sgitem" v-for="item in songs" :to="'/song?id='+item.id" :key="item.id">
      <div class="sgfr">
        <div class="sgchfl">
          <div class="sgtitle">
            {{item.name}}<span>{{item.song.alias[0]!==undefined?('('+item.song.alias[0]+')'):''}}</span></div>
          <div class="sginfo"><i class="fa"></i>{{item.song.artists[0].name+' - '+item.song.album.name}}</div>
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
    props: ['songs'],
    name: "myNewsong"
  }
</script>

<style scoped>

</style>
