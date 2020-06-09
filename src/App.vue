<template>
  <div id="app">
    <Header />
    <div class="maintop">
      <div class="wrapper">
        <FigureMask :isMobile="isMobile" :windowWidth="windowWidth" />
        <i v-scroll-to="'#ad1'" class="fas fa-chevron-down morearr" />
      </div>
    </div>
    <hr id="ad1" />
    <div class="wrapper ad">
      <AdArea
        :isMobile="true"
        path="/1006274/coronavirus_mob_home_300x250_t"
        :size="[[1, 1], [300, 250]]"
        id="div-gpt-ad-1583482179290-0"
        data-aos="fade"
      />
      <AdArea
        :isMobile="false"
        path="/1006274/coronavirus_pc_home_970x250_t"
        :size="[[1, 1], [970, 250]]"
        id="div-gpt-ad-1583482097742-0"
        data-aos="fade"
      />
    </div>
    <div class="wrapper">
      <MainContent :content="contentArticle[0]" />
      <Compare />
      <Case :isMobile="isMobile" />
      <article class="area">
        <h2>危老改建潮正夯 民眾買單熱絡 帶動全新商機</h2>
        <p>新北市城鄉發展局都更處主任祕書李擇仁表示，危老上路至今，已有足夠實例證明，這套政策克服了民眾對都更的兩大痛點：遙遙無期、整合困難。與三年前相比，危老屋主開始變得敢想、敢行動了。</p>
        <p>住在板橋太和街的胡婕筠，多年來飽受房屋漏水之苦，花了大筆費用整修，依舊治標不治本。去年四月，得知危老重建容積獎勵優渥，胡婕筠與先生決定以自家的透天厝重啟危老計畫，沒想到經過初評與送件後，很順利地獲得新北市政府核定容積獎勵22％，前後花不到半年。</p>
        <p>危老遍地開花，也帶出了「平台業者」全新商機。舉例來說，信義房屋關係企業安信建經，就開始切入危老市場的「全案管理」，為有意申請危老重建的地主，進行「一條龍」的後續服務。這類公司更像是一個「平台」，業者可串聯建築師、地政士、銀行、營造廠等，宛如另開一條以危老重建為起點的全新產業鏈。</p>
        <p>危老重建終究只是都更大計底下的一條快速通道，在飆速衝刺之後，包括近來外界漸有疑慮的「滿街紙片屋」，或者可能造成畸零地、地籍零碎、不利都市景觀等問題，確實都該認真思考。</p>
        <div class="readmore">
          <a href="#" target="_blank">看完整文章</a>
        </div>
      </article>
      <Sop />
      <MainContent :content="contentArticle[1]" />
      <Map :windowWidth="windowWidth" />
    </div>
    <div class="wrapper ad">
      <AdArea
        :isMobile="true"
        path="/1006274/coronavirus_mob_home_300x250_m"
        :size="[[1, 1], [300, 250]]"
        id="div-gpt-ad-1584416405870-0"
        data-aos="fade"
      />
      <AdArea
        :isMobile="false"
        path="/1006274/coronavirus_pc_home_970x250_m"
        :size="[[1, 1], [970, 250]]"
        id="div-gpt-ad-1584416279913-0"
        data-aos="fade"
      />
    </div>
    <div v-if="sliderData" class="area slider">
      <div class="wrapper"><h2>延伸閱讀</h2></div>
      <BtnetSlider :sliderData="sliderData" />
    </div>
    <BtnetFooter :goTop="true" />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header'
import FigureMask from './components/FigureMask'
import AdArea from './components/AdArea'
import MainContent from './components/MainContent'
import Compare from './components/Compare'
import Case from './components/case/Case'
import Sop from './components/Sop'
import Map from './components/map/Map'
import BtnetSlider from './components/BtnetSlider'
import BtnetFooter from './components/BtnetFooter'

import contentimage1 from './assets/images/areaimg.png'
import contentimage3 from './assets/images/areaimg3.png'

import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
  name: 'App',
  components: {
    Header,
    FigureMask,
    AdArea,
    MainContent,
    Compare,
    Case,
    Sop,
    Map,
    BtnetSlider,
    BtnetFooter
  },
  data() {
    return {
      windowWidth: null,
      isMobile: null,
      contentArticle: [
        {
          article: '<p>漏水屋翻身百坪宅、舊倉庫變成唯美宅，「都更特快車」正在改變城市樣貌，以及許多人的家。</p><p>當了一輩子的土地代書，李佩勲從沒想到，自己的人生竟然會在50歲後，迎來這麼大的改變。</p><p>改變的觸媒，是2017年上路的「危老重建」政策。</p><p>這兩年，在他的辦公室裡，各方地主絡繹不絕地上門，每逢周末，還得抽空參加建商主辦的危老說明會，成了台下爆滿聽者口中的李老師。</p><p>三年前，簡稱《危老條例》的《都市危險及老舊建築物加速重建條例》上路，這部新法被喻為「都更高速公路」，熟悉都更的他，自然也快速上手，很快轉型為「危老推動師」，代書人生像忽然轉個彎，駛上了沒有紅燈的高速公路。</p><p>李佩勲說，《危老條例》上路後，感受到不少原本已經打消重建念頭的老屋主人，又開始動了起來。有專業又富服務熱忱的他，透過地主互相介紹，從原本「每天煩惱沒案子」的失意代書，變身為「每天忙到沒時間」的危老推動一哥。</p>',
          image: contentimage1
        },
        {
          title: '專訪內政部次長>>善用危老成功經驗',
          article: '<p>「連總統都在關心，今年要做多少案量？」內政部政務次長花敬群說。那是在2018年初，小英總統給了他一年衝到320案的目標，2019年底結算，當年就有433件申請案量。</p><p>回想推動過程，花敬群坦言，當時很多人並不看好，但「我就是要讓團結的社區，有一條都更高速公路。」</p><p>《危老條例》施行期間只有十年，在推動都更策略上，危老政策固然是為因應潛在災害風險及高齡化社會需求，要加速危老重建，但核心目標是希望藉此喚起民眾對房屋結構安全的重視。</p><p>「我在《危老條例》穿插兩個伏筆，其實是為了《都更條例》再鬆綁所做的預備。」一是容積獎勵明確化，只有行政審查一關；二是只要不轉售，房屋稅減半徵收12年。</p><p>過去地主之間常因容積獎勵的模糊空間陷入談判僵局，容易產生釘子戶，但在危老的作法是白紙黑字規定容積獎勵額度，不用再經審議委員審核，他希望未來都更審議流程也比照辦理，可大幅提升行政效率。</p><p>「我希望有一天，危老與都更在民眾心理可以平起平坐，不要再讓民眾覺得『都更好難』。」花敬群衷心地說。</p>',
          image: contentimage3,
          url: '#'
        }
      ],
      sliderData: null
    }
  },
  methods: {
    checkScreen() {
      const clientWidth = document.documentElement.clientWidth;
      if (clientWidth !== this.windowWidth) {
        this.isMobile = /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ? true : false;
        this.windowWidth = clientWidth;
      }
    }
  },
  mounted() {
    this.checkScreen();
    window.addEventListener('resize', this.checkScreen);
    axios.get('data.json')
    .then(response => {
      this.sliderData = response.data;
    })
    .catch(error => {
      console.log(error);
    });
    AOS.init();
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkScreen);
  }
}
</script>

<style src='./assets/css/style.css'></style>
<style>
.morearr {
  position: absolute;
  font-size: 35px;
  color: white;
  left: 50%;
  bottom: 0;
  margin-left: -17.5px;
  cursor: pointer;
  opacity: 1;
  transition: .5s;
  -webkit-animation-name: moveBottom;
  animation-name: moveBottom;
  animation-iteration-count: infinite;
  animation-duration: 1s;
}
@keyframes moveBottom {
  0% {
    -webkit-transform: translate(0, -25%);
    -ms-transform: translate(0, -25%);
    transform: translate(0, -25%);
  }
  50% {
    -webkit-transform: translate(0, -5%);
    -ms-transform: translate(0, -5%);
    transform: translate(0, -5%);
  }
  100% {
    -webkit-transform: translate(0, -25%);
    -ms-transform: translate(0, -25%);
    transform: translate(0, -25%);
  }
}
hr#ad1 {
  padding-top: 60px;
  margin: 0;
  border: none;
}

@media (hover: hover) {
  .morearr:hover {
    opacity: .7;
  }
}

@media screen and (max-width: 480px) {
  hr#ad1 {
    padding-top: 50px;
  }
}

</style>
