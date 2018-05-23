<template>
  <div style="height:100%">
    <section>
      <myHeader></myHeader>
      <div class="main">
        <nav class="u-tab">
          <ul class="tabtitle">
            <li class="tab-list" :class="{active:currentTab=='myPersonalized'}">
              <a href="javascript:void(0)" @click="toggleTab('myPersonalized')">
                <div class="tabtxt">
                  <span>推荐音乐</span>
                </div>
              </a>
            </li>
            <li class="tab-list" :class="{active:currentTab=='myHot'}">
              <a href="javascript:void(0)" @click="toggleTab('myHot')">
                <div class="tabtxt">
                  <span>热歌榜</span>
                </div>
              </a>
            </li>
            <li class="tab-list" :class="{active:currentTab=='mySearch'}">
              <a href="javascript:void(0)" @click="toggleTab('mySearch')">
                <div class="tabtxt">
                  <span>搜索</span>
                </div>
              </a>
            </li>
          </ul>

        </nav>
        <!--主体部分-->
        <div class="tabct">
          <!--动态组件-->
          <component :is="currentTab" keep-alive></component>
        </div>
      </div>
    </section>
  </div>

</template>

<script>
  import myHeader from '~/components/myHeader'
  import myPersonalized from '~/components/tab/myPersonalized'
  import myHot from '~/components/tab/myHot'
  import mySearch from '~/components/tab/mySearch'

  export default {
    components: {
      myHeader,
      myPersonalized,
      myHot,
      mySearch
    },
    data(){
      return{
        currentTab:'myPersonalized'
      }
    },
    methods:{
      toggleTab:function (tab) {
        this.currentTab = tab
      }
    }
  };
</script>

<style>
</style>
