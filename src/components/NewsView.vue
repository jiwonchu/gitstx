<template>
  <section class="news">
    <div class="inner clearfix">
      <!-- {{ntdata}} -->
      <div class="news-box">
        <h3>공지사항</h3>
        <ul class="news-list">
          <!-- 받아온 데이터 순서 번호 하나하나 -->
          <li v-for="(item,index) in ntdata" v-bind:key="index">
            <!-- {{item}} -->
            <a v-bind:href="item.url"><span>{{item.title}}</span></a>
          </li>
          <!-- <li><a href="#"><span>에스티엑스건설자산관리 주식회사 해산결의에 따른 채권신고 안내 공고 (2차)</span></a></li>
          <li><a href="#"><span>에스티엑스건설자산관리 주식회사 해산결의에 따른 채권신고 안내 공고 (1차)</span></a></li>
          <li><a href="#"><span>2021년도 협력업체 모집공고</span></a></li>
          <li><a href="#"><span>STX건설 상호 사용 관련 안내</span></a></li> -->

        </ul>
      </div>
      <!-- {{nsdata}} -->
      <div class="news-box">
        <h3>보도자료</h3>
        <ul class="news-list">
          <li v-for="(item,index) in nsdata" v-bind:key="index">
            <a v-bind:href="item.url"><span>{{item.title}}</span></a>
          </li>         

        </ul>
      </div>
    </div>

  </section>
</template>

<script>
  export default {
    props: ['ntdata', 'nsdata']
  }
</script>

<style>
  .news {
    position: relative;
    height: 480px;
  }

  .news .inner {
    z-index: 9;
  }

  .news::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 50%;
    height: 100%;
    background-color: #ed1c24;
  }

  .news::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 0;
    width: 50%;
    height: 100%;
    background-color: #58595b;
  }

  .news-box {
    width: 50%;
    float: left;
    padding: 55px 0;
  }

  .news-box:first-child {
    padding-right: 110px;
  }

  .news-box:last-child {
    padding-left: 110px;
  }

  .news-box h3 {
    font-size: 32px;
    color: #fff;
    font-weight: 300;
    margin-bottom: 45px;
  }

  .news-list {}

  .news-list li {
    padding: 25px 0;
    border-top: 1px solid rgba(255, 255, 255, 0.4);

  }

  .news-list li:last-child {
    border-bottom: 1px solid rgba(255, 255, 255, 0.4);
  }

  .news-list li a {
    position: relative;
    display: block;

  }

  .news-list li a::after {
    content: '';
    position: absolute;
    right: 0;
    top: 0;
    transform: translateX(-50%);
    width: 48px;
    height: 23px;
    background: url('../assets/images/bg_common.png')no-repeat;
    background-position: 0px -49px;
  }

  .news-list li a span {
    display: inline-block;
    width: 80%;
    font-size: 16px;
    color: #fff;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
    font-weight: 200;

  }
</style>