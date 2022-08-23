<template>
  <!-- 안내창 -->
  <ModalPop />
  <div class="wrap">
    <!-- header -->
    <HeaderView v-bind:gnbdata="gnbData"/>
    <!-- visual -->
    <VisualView></VisualView>
    <!-- part -->
    <PartView></PartView>
    <!-- news -->
    <NewsView v-bind:ntdata="noticeData" v-bind:nsdata="newsData"></NewsView>
    <!-- help -->
    <CspartView></CspartView>
    <!-- about -->
    <AboutView></AboutView>
    <!-- footer -->
    <FooterView></FooterView>
  </div>
</template>

<script>
  import {
    ref
  } from 'vue';
  //vue라는 곳에서 ref 라는 기능을 가지고오겠다

  import ModalPop from '@/components/ModalPop.vue';
  import HeaderView from '@/components/HeaderView.vue';
  import VisualView from '@/components/VisualView.vue';
  import PartView from '@/components/PartView.vue';
  import NewsView from '@/components/NewsView.vue';
  import CspartView from '@/components/CspartView.vue';

  import AboutView from '@/components/AboutView.vue';
  import FooterView from '@/components/FooterView.vue';



  export default {
    name: 'App',
    components: {
      ModalPop,
      HeaderView,
      VisualView,
      PartView,
      NewsView,
      CspartView,
      AboutView,
      FooterView
    },
    setup() {
      //gnb 메뉴 데이터
      const gnbData = [
        {
          mainlink:'#',
          maintxt:'회사소개',
          subdata:[
            {sublink:'#',subtxt:'인사말'},
            {sublink:'#',subtxt:'STX건설'},
            {sublink:'#',subtxt:'STX건설화'},
            {sublink:'#',subtxt:'STX건설연혁'},
            {sublink:'#',subtxt:'조직안내'},
            {sublink:'#',subtxt:'윤리경영'},
            {sublink:'#',subtxt:'안전·환경·품질경영'},
            {sublink:'#',subtxt:'찾아오시는길'}
          ]
        },
        {
            mainlink:'#',
          maintxt:'사업분야',
          subdata:[
            {sublink:'#',subtxt:'건축사업'},
            {sublink:'#',subtxt:'주택사업'},
            {sublink:'#',subtxt:'토목사업'},
            {sublink:'#',subtxt:'플랜트/공작기계사업'},
            {sublink:'#',subtxt:'해외사업'}
           
          ]
        },
        {
           mainlink:'#',
          maintxt:'사회공헌',
          subdata:[
            {sublink:'#',subtxt:'나눔의생각'},
            {sublink:'#',subtxt:'주요활동분야'},
            {sublink:'#',subtxt:'활동현황'}
           
           
          ]
        },
        {
          mainlink:'#',
          maintxt:'홍보센터',
          subdata:[
            {sublink:'#',subtxt:'홍보동영상'},
            {sublink:'#',subtxt:'홍보브로슈어'},
            {sublink:'#',subtxt:'STX건설뉴스'}
          ]
        },
        {
              mainlink:'#',
          maintxt:'고객지원',
          subdata:[
            {sublink:'#',subtxt:'자주묻는질문'},
            {sublink:'#',subtxt:'고객문의'},
          
              ]
                      },
        {
          mainlink:'#',
          maintxt:'채용정보',
          subdata:[
            {sublink:'#',subtxt:'채용안내'},
            {sublink:'#',subtxt:'채용공고'},
            {sublink:'#',subtxt:'채용FAQ'},
          ]
        }
      ];

      const noticeData = [{
          url: 'a.html',
          title: '에스티엑스건설자산관리 주식회사 해산결의에 따른 채권신고 안내 공고 (2차)'
        },
        {
          url: 'b.html',
          title: '에스티엑스건설자산관리 주식회사 해산결의에 따른 채권신고 안내 공고 (1차)'
        },
        {
          url: 'c.html',
          title: '2021년도 협력업체 모집공고'
        },
        {
          url: 'd.html',
          title: 'STX건설 상호 사용 관련 안내'
        }
      ];


      const newsData = [{
          url: 'k.html',
          title: 'STX건설, 춘천 레고랜드 테마파크 시공사 ‘선정’'
        },
        {
          url: 'i.html',
          title: 'STX건설, 2018년 성장 청신호'
        }
      ];
      let showModal = ref(true);
      //값이 바뀌는 걸 계속 감시한다 ->ref 외에 3가지 더있음
      const closeModal = () => {
        //모달창 닫기변수 변경
        showModal.value = false;
        //ref로 감쌌으면 value로 호출해야한다.
        console.log(showModal.value);
      }
      const showMessage = (_txt) => {

        alert(_txt);
      }

      return {
        noticeData,
        newsData,
        showModal,
        closeModal,
        showMessage,
        gnbData

      }
    }
  }
</script>

<style>
  @charset 'utf-8';

  #app {}

  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap');

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  ul,
  li {
    list-style: none;
  }

  a {
    text-decoration: none;
    color: #333;
  }

  /* //#의 의미 16진수// */

  img {
    vertical-align: middle;
    border: 0;
  }

  html {
    font-size: 16px;

  }

  body {
    font-family: 'Noto Sans KR', Helvetica, '맑은 고딕', 'malgun gothic', 'Apple SD Gothic Neo', sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 1.4;
    letter-spacing: 0.64px;
    color: #444;
  }

  /* 공통구역 */

  .clearfix::after {
    content: '';
    position: relative;
    display: block;
    width: 100%;
    clear: both;
  }

  .inner {
    position: relative;
    display: block;
    width: 1200px;
    margin: 0 auto;
  }

  .wrap {
    padding-top: 80px;
  }

  /* 안내창 */
  .modal-wrap {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    z-index: 99999;
  }

  .modal-main {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 550px;
    height: 400px;
    background-color: #fff;
    border-radius: 8px;
    padding: 10px;
    box-shadow: 0px 0px 15px 0px rgb(0 0 0/ 70%);
    border: 5px solid rgba(0, 0, 0, 0.1);

  }

  .modal-main h1 {
    font-size: 30px;
    font-weight: 600;
    text-align: center;
    color: #000;
    padding: 20px 0;
  }

  .modal-main p {
    text-align: center;
    font-weight: 300;
    font-size: 16px;
    color: #111;
    line-height: 1.8;
  }

  .modal-main b {
    font-weight: 600;
    text-decoration: underline;
    color: #ed1c24;
  }

  .modal-main strong {
    font-weight: 600;
    text-decoration: underline;
    color: #ed1c24;
  }

  .modal-close {
    position: absolute;

    right: 20px;
    top: 20px;
    border: 0;
    cursor: pointer;
    font-size: 24px;
    background: transparent;
    color: #999;
    transition: transform 0.3s;
  }

  .modal-close:hover {
    transform: rotate(90deg);
  }

  /* 내용별 Section */

  /* 상단 */



  /* 비주얼 */



  /* 파트 */



  /* 소식 */



  /* 고객센터 */



  /* 소개 */



  /* 하단 */
</style>