<template>
  <div class="hmhot">
    <div class="hotop">
      <div class="hotopct">
        <div class="hottime">更新日期：{{getMonth}}月{{getdate}}日</div>
      </div>
    </div>
    <div class="hotcont">
      <myHotSong :songs="hotSongs"></myHotSong>
    </div>
    <div @click="getmore()" class="getmore">{{bottomText}}</div>
  </div>


</template>

<script>
  import axios from "axios";
  import myHotSong from "../song/myHotsong";

  export default {
    name: "myHot",
    components: {
      myHotSong,

    },
    data() {
      return {
        getdate: '',
        getMonth: '',
        hotSongs: [],
        bottomText: '加载更多...',
        pageNo: 1,
        totalCount: '',
        alldata:[],
        pageCount:0
      };
    },
    methods:{
      getmore() {
        this.hotSongs = this.hotSongs.concat(this.alldata.slice(this.pageCount*20,this.pageCount*20+20));
        this.pageCount++;
        if (this.pageCount===this.totalCount) {
          this.bottomText='已全部加载完'
        }
      }
    },
    mounted() {
      axios.get("http://localhost:3000/top/list?idx=1").then((res) => {
        this.alldata = res.data.playlist.tracks;
        this.totalCount= (this.alldata.length+7)/20;
        this.getmore();
      });
      var date = new Date();
      this.getdate = date.getDate();
      this.getMonth = date.getMonth() + 1;
    }

  };
</script>

<style scoped>
</style>
