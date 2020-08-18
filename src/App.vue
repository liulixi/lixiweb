<template>
  <div id="app">
    <main class="main">
      <section class="list-item">
        <div class="item-image">
          
        </div>
        <div class="item-text">
          <div class="text-title">你好，<br>我是刘立希，<br>一个非典型程序员。</div>
          <div class="text-desc">爱好足球、吉他和编程。</div>
        </div>
      </section>
      
      <section class="list-item">
        <div class="item-image">
          <img src="./assets/img/spacesea.jpg" />
        </div>
        <div class="item-text">
          <div class="text-title">天行健，君子当自强不息</div>          
        </div>
      </section>
      <section class="list-item">
        <div class="item-image">
        </div>
        <div class="item-text">
          <div class="text-title">地势坤，君子当厚德载物</div>          
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import earth from './components/echarts/Earth'

export default {
  name: "App",
  components: {
    'earth':earth
  },
};
</script>

<style>
@import "assets/css/base.css";
</style>
