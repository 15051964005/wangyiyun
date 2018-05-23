<template>
  <div class="htSearch">
    <form class="formInput" action="#">
      <div class="divInput">
        <i class="fa fa-search"></i>
        <input type="search" name="search" class="input"
               placeholder="搜索歌曲、歌手、专辑" v-model="value" autocomplete="off">
        <!--<label class="holder">搜索歌曲、歌手、专辑</label>-->
        <figure class="close">
          <i class="fa fa-close"></i>
        </figure>
      </div>
    </form>
    <div class="htDefault">
      <section class="hotlist">
        <h3 class="title">热门搜索</h3>
        <ul class="list">
          <li v-for="(item,index) in hotSearchs" class="item" :key="index">
            <a class="link" href="javascript:void(0);">{{item.first}}</a>
          </li>
        </ul>
      </section>
      <!--<section class="history">-->
        <!--<ul class="list">-->
          <!--<li>-->
            <!--<i class="fa fa-history"></i>-->
            <!--<div class="histy">-->
              <!--<span class="link"></span>-->
              <!--<figure class="close"><i class="fa fa-close"></i></figure>-->
            <!--</div>-->
          <!--</li>-->
        <!--</ul>-->
      <!--</section>-->
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: "mySearch",
    data() {
      return {
        hotSearchs:[],
        value:''
      }
    },
    mounted(){
      axios.get("http://localhost:3000/search/hot").then((res) => {
        this.hotSearchs = res.data.result.hots
      });
    }
  }
</script>

<style scoped>

</style>
