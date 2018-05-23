<template>
  <div class="homeremd">
    <h2 class="remd_title">
      推荐歌单
    </h2>
    <div class="remd_songs">
      <ul class="remd_ul">
        <nuxt-link class="remd_li" v-for="songList in songLists1" :key="songList.id"
                   :to="'/playlist?id='+songList.id">
          <div class="remd_img">
            <img :src="songList.picUrl" alt="">
            <span class="remd_count"><i
              class="fa fa-headphones"></i>{{Math.floor(songList.playCount/1000)/10+'万'}}</span>
          </div>
          <p class="remd_text">{{songList.name}}</p>
        </nuxt-link>
      </ul>
      <ul class="remd_ul">
        <nuxt-link class="remd_li" v-for="songList in songLists2" :key="songList.id"
                   :to="'/playlist?id='+songList.id">
          <div class="remd_img">
            <img :src="songList.picUrl" alt="">
            <span class="remd_count"><i
              class="fa fa-headphones"></i>{{(songList.playCount/10000).toFixed(1)+'万'}}</span>
          </div>
          <p class="remd_text">{{songList.name}}</p>
        </nuxt-link>
      </ul>
    </div>
    <h2 class="remd_title">
      最新音乐
    </h2>
    <div class="remd_newsongs">
      <mySong :songs="newSongs"></mySong>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import mySong from '../song/myNewsong';
  export default {
    name: "myPersonalize",
    components:{
      mySong
    },
    data() {
      return {
        songLists: [],
        songLists1: [],
        songLists2: [],
        newSongs: []
      }
    },
    mounted() {
      axios.get('http://localhost:3000/personalized').then((res) => {
        this.songLists = res.data.result;
        this.songLists1 = this.songLists.slice(0, 3);
        this.songLists2 = this.songLists.slice(3, 6);
      });
      axios.get('http://localhost:3000/personalized/newsong').then((res) => {
        this.newSongs = res.data.result;
      });
    }
  }

</script>

<style scoped>

</style>
