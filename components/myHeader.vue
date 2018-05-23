<template>
    <div class="header">
      <!--全局顶部导航栏-->
      <nav class="navbar">
        <div>
          <img src="~/assets/img/logo.png" alt="">
        </div>
      </nav>
    </div>
</template>

<script>
    export default {
        name: "myHeader"
    }
</script>

<style scoped>
  .header{
    width: 100%;
    height: 64px;
  }
  .navbar{
    width: 100%;
    height: 64px;
    position: fixed;
    top: 0;
    left: 0;
    background: #d43c33;
    padding: 0 10px;
    z-index: 100;
    display: flex;
    align-items: center;
  }
  .navbar img{

  }
</style>
