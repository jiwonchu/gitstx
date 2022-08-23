<template>
  <header class="header">
    <div class="inner">
      <a href="#" class="logo">stx건설</a>
      <nav class="gnb clearfix">

        <ul class="depth1">
          <li v-for="(item,index) in gnbdata" :key="index">
            <a v-bind:href="item.mainlink">{{item.maintxt}}</a>
            <ul class="depth2">
              <li v-for="(subitem,subindex) in item.subdata" :key="subindex">
                <a :href="subitem.sublink">{{subitem.subtxt}}</a>
              </li>
            </ul>
          </li>

        </ul>
      </nav>
      <div class="lang">
        <a href="#">ENG</a>
        <i class="lang-bar"></i>
        <a href="#" class="lang-active">KOR</a>
      </div>
    </div>
  </header>
</template>

<script>
  import $ from 'jquery';
  import {
    onMounted
  } from 'vue';
  export default {
    // props를 받겠다.
    props: ['gnbdata'],
    setup() {
      // vue에서 화면에 html등록시 실행
      onMounted(() => {
        //.header를 저장한다.
        let header = $('.header');
        let gnb = $('.gnb');
        //펼쳐졌을때의 높이값
        let gnbMaxHeight = gnb.outerHeight();
        //닫혔을때의 높이값
        let gnbMinHeight = header.outerHeight();
        //기본 header 의 높이값 적용
  header.css('height',gnbMinHeight)
  // = header height :80px 
  console.log(gnbMaxHeight);
  console.log(gnbMinHeight);



  console.log( gnb. height() );
  //콘솔창에 높이값인 436이 뜬다.
  console.log( gnb. outerHeight() );
  //보더 마진 패딩 포함한 값 출력

  gnb.mouseenter(function () {
    header.css('height',gnbMaxHeight);
  });
  gnb.mouseleave(function () {
    header.css('height',gnbMinHeight);
    depth_1_Li.eq(1).find('>a').addClass('depth1-focus');
  });
  //주메뉴 포커스 기능
  let depth_1_Li = $('.depth1 >li');
   //두번째 것에 a 태그를 찾고 depth 1 포커스에 유지
  $.each(depth_1_Li, function () {
    $(this).mouseenter(function () {
      depth_1_Li.find('>a').removeClass('depth1-focus');
      //li의 > a를 찾는다.
      // $(this).find('>a').css('color','#ed1c24'); 추천하지않는방법
      $(this).find('>a').addClass('depth1-focus');

    });
    $(this).mouseleave(function () {
      // $(this).find('>a').css('color','#000');
      $(this).find('>a').removeClass('depth1-focus');
    });
  })
      });
      return {

      }
    }
  }
</script>

<style>
  .header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    overflow: hidden;
    height: 80px;
    transition: height 0.5s;
    z-index: 9999;
    box-shadow: 0px 0px 7px 0px rgb(0 0 0 / 20%);

  }

  .header-open {
    height: 400px;
  }

  /* .header:hover{
  height: 400px;
} */
  .header::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 0;
    width: 100vw;
    height: 80px;
    background-color: #fff;
    transform: translateX(-50%);

  }

  .header .inner {
    background-color: ;
  }

  .logo {
    position: absolute;
    left: -300px;
    top: 20px;
    width: 150px;
    height: 39px;
    display: block;
    background: url('../assets/images/logo.png')no-repeat center;
    background-size: cover;
    font-size: 0;

  }

  .gnb::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 80px;
    transform: translateX(-50%);
    display: block;
    width: 100vw;
    height: calc(100% - 80px);
    background-color: rgba(0, 0, 0, 0.5);
  }

  .gnb {

    position: relative;
  }

  .depth1 {
    position: relative;
    display: table;
    table-layout: fixed;
    width: calc(180px * 6 - 70px);
    margin: 0 auto;
  }

  .depth1>li {
    /* 
   */
    width: 180px;
    display: table-cell;
    /* background-color: yellow; */
  }

  .depth1>li>a {
    position: relative;
    font-size: 19px;
    color: #000;
    font-weight: 500;
    line-height: 80px;
  }

  .depth1>li>a::after {
    content: '';
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    bottom: 0;
    width: 0%;
    height: 4px;
    background: #ed1c24;
    transition: width 0.5s;
  }

  .depth1-focus {
    color: #ed1c24 !important;
  }

  .depth1-focus::after {
    width: 100% !important;

  }

  .depth2 {
    padding-top: 40px;
    padding-bottom: 20px;
  }

  .depth2 a {
    display: inline-block;
    font-size: 15px;
    color: #fff;
    margin-bottom: 15px;

  }

  .depth1>li:last-child {
    width: 70px;
  }

  .lang {
    position: absolute;
    left: calc(100% + 100px);

    top: 34px;
    font-size: 0;
    white-space: nowrap;

  }

  .lang a {
    display: inline-block;
    font-size: 15px;
    color: #888;
    font-weight: 500;
    text-transform: uppercase;
    /* margin-right: 20px; */
  }

  /* .lang-bar::after{
  position: absolute;
content: '';
display: block;
right:63px;
top:6px;
width:1px;
height: 11px;
background-color: #999;

} */

  .lang-bar {
    display: inline-block;
    width: 1px;
    height: 9px;
    background-color: #999;
    margin: 0 10px;
  }

  .lang .lang-active {

    color: #000;
  }

  .depth2 {}
</style>