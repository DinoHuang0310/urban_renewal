<template>
  <div class="map area">
    <h2>完整案例>>透天厝華麗轉身</h2>
    <div class="maparea">
      <div>
        <img src="../../assets/images/taiwanmap.png" alt="taiwan" />
        <ul class="mappoint">
          <li
            v-for="list in mapcontent"
            :key="list.index"
            :data-title="list.placeCh"
            :class="list.placeEn"
            @click="handleDisplay(list.placeEn)"
          >
            <img src="../../assets/images/mappoint.png" :alt="list.placeCh" />
          </li>
        </ul>
      </div>
      <ul class="maparticle">
        <MapList
          v-for="list in mapcontent"
          :key="list.index"
          :mapcontent="list"
          :windowWidth="windowWidth"
          :activeList="activeList"
        />
      </ul>
    </div>
    <div class="readmore"><a href="#" target="_blank">看完整文章</a></div>
  </div>
</template>

<script>
import MapList from './MapList'

export default {
  components: {
    MapList
  },
  props: {
    windowWidth: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      mapcontent: [
        {
          placeCh: '宜蘭',
          placeEn: 'yilan',
          title: '宜蘭老屋第三代',
          article: '<p>「如果說礁溪溫泉區開發了99％，這條巷子就是被遺忘的那1％。」陳奕安是屋主陳家第三代。</p><p>「本來我想推動整條巷子的都更。」他花了一年時間和鄰居溝通，成功獲得其中八戶人家的同意，「大家一開始都很熱情，直到最後談分配……。」</p><p>當時建商開出五五分潤相對合理的條件，部分居民卻堅持要八二分。分配談不攏，都更案最後破局。</p><p>「後來我才知道，原來小坪數可以用危老的方式改建！」直到危老政策上路，他找到解方，全心投入危老申請。</p><p>「如果只是拉皮裝修也要花3、4百萬元，多花個兩三倍就能重建，還可以增加樓層，不是更划算？」</p><p>原本兩層樓的透天厝，將改建成五層樓的電梯大樓，具生意頭腦的陳奕安，算盤更是打不完。「我打算把一樓做店面出租，二樓自住，三到五樓做民宿，扣掉人事及營運成本，預估一個月有十萬元進帳。」</p><p>他希望能拿自家危老案為範例，邀請附近鄰居一起改建。「說不定，可以成為比羅東夜市更熱鬧的商圈。」</p>'
        },
        {
          placeCh: '台中',
          placeEn: 'taichung',
          title: '台中上班族夫妻',
          article: '<p>「剛開始，只是想重建為一棟通風流暢、採光自然，有自己風格的住家，」45歲的屋主張惠淇說，她和先生都是藥師。</p><p>九年前，他們買下這棟老屋，想著要重建一棟不一樣的房子，但探詢不少建築師，得到的回覆都是「不可能」，最主要是基地面積小，以他們有限的重建預算，建築師幾乎毫無利潤。</p><p>直到2017年，透過朋友輾轉認識了建築師劉承鑫，夢想清單列了一堆，年輕的劉承鑫倒也大膽接單。而那一年，《危老條例》正好施行，成為夫妻倆圓夢的另一著力點。</p><p>「把危老重建計畫書送給銀行審查後420萬元的營造費用，拿到了百分之百全額貸款，且利率僅2.3％。」</p><p>2018年4月，送件申請危老重建，當年6月就核准，並在8月開始施工，去年第四季完工，前後僅僅耗時一年半。</p><p>負責營造施工的百唐營造老闆林永春說，這是他蓋過面積最小、複雜度最高的房子，他打趣說，一樓室內只有十一坪，竟然是三層之中最大的面積。</p>'
        },
        {
          placeCh: '台南',
          placeEn: 'tainan',
          title: '台南76歲奶奶',
          article: '<p>距離台南高鐵站15分鐘的車程，這棟三層樓的透天厝，屋齡超過50年；過去，孫奶奶一家人一直在這裡生活。</p><p>建造時間早，沒有電梯，對年歲已高的孫奶奶來說，三層樓爬上爬下終究吃力，想要住在有電梯的房子裡，讓孫奶奶動了改建的念頭。</p><p>「我們花了幾個月的時間與奶奶溝通，了解她的需求。」富喬建設執行長兼承辦設計師鄒宇南表示，由於奶奶年紀大了，坪數不需要太大，怕難整理，手上的預算也不多。在多方考量後，決定以跟建商合建的方式進行改建，並且於今年4月正式簽約。</p><p>以孫奶奶的案例來說，取得獎勵容積後，原本三層樓的老屋，可以改建成六層樓的電梯大樓，總建造成本約2千8百萬元；而且，建設成本完全由建商負擔。</p><p>而空間分配的部分，奶奶只留下頂樓一層自住，其餘二到五樓則交由建設公司出售。奶奶雖然無法享受銷售利潤，但建商會支付她約3百萬元左右的養老金，改建期間的租屋費用也全由建商負擔。</p>'
        }
      ],
      activeList: 'yilan'
    }
  },
  methods: {
    handleDisplay(target) {
      if(this.windowWidth < 1024) this.activeList = target;
    }
  }
}
</script>

<style>
.maparea {
  display: flex;
  position: relative;
  justify-content: center;
  margin: 1em 0;
}
.maparea > div {
  position: relative;
  display: inline-block;
  width: 36%;
}
.maparea img {
  display: block;
  width: 100%;
}
.maparea ul {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}

/* map point */
.maparea ul.mappoint li {
  position: absolute;
  width: 6%;
}
.maparea ul.mappoint li:after {
  content: attr(data-title);
  position: absolute;
  display: block;
  white-space: nowrap;
  left: 50%;
  bottom: 0;
  transform: translate(-50%, 100%);
}
.maparea ul.mappoint li.yilan {
  top: 15%;
  right: 14%;
}
.maparea ul.mappoint li.taichung {
  top: 27%;
  left: 33%;
}
.maparea ul.mappoint li.tainan {
  top: 60%;
  left: 14%;
}
.maparea ul li article h4 {
  font-size: 1.2em;
  color: #008c96;
  cursor: pointer;
  margin: 0;
  padding: 0.5em 1em;
  background: #efefef;
  transition: .5s;
}
.maparea ul li article div {
  padding: 0 1em;
}

@media (hover: hover) {
  .maparea ul li article h4:hover {
    color: white;
    background: #008c96;
  }
}

@media screen and (min-width: 1024px) {
  /* map article */
  .maparea ul.maparticle li {
    position: absolute;
    width: 360px;
    text-align: left;
  }
  .maparea ul.maparticle li.yilan {
    transform: translate(105%, 0);
    top: 15%;
    right: 37%;
  }
  .maparea ul.maparticle li.taichung {
    transform: translate(-113%, 0);
    top: 26%;
    left: 43%;
  }
  .maparea ul.maparticle li.tainan {
    transform: translate(-110%, 0);
    top: 60%;
    left: 37%;
  }
}

@media screen and (min-width: 1024px) {
  .maparea ul.maparticle li.taichung {
    top: 15%;
  }
  .maparea ul.maparticle li.tainan {
    left: 39%;
  }
  .maparea ul.maparticle li span {
    display: none;
  }
}

@media screen and (max-width: 1023px) {
  .maparea {
    justify-content: space-around;
    align-items: center;
  }
  .maparea > div {
    width: 40%;
  }
  .maparea ul.maparticle {
    position: relative;
    width: 50%;
  }
  .maparea ul.maparticle li {
    position: relative;
  }
  .maparea ul li article h4 {
    padding: 0.4em;
    font-size: 1.1em;
  }
  .maparea ul li span {
    position: absolute;
    top: -2px;
    left: 0;
    transform: translate(0, -100%);
    padding: 0.2em 0.8em;
    color: white;
    background: #008c96;
  }
  .maparea ul li article div {
    padding: 0 0.4em;
  }
}

@media screen and (max-width: 640px) {
  .maparea {
    flex-wrap: wrap;
  }
  .maparea > div {
    width: 50%;
  }
  .maparea ul.mappoint li {
    width: 10%;
  }
  .maparea ul.maparticle {
    margin-top: 1em;
    width: 100%;
  }
  .maparea ul li article h4 {
    font-size: 1em;
  }
  .maparea ul li span {
    font-size: .9em;
  }
  .maparea ul.mappoint li.taichung {
    top: 24%;
    left: 29%;
  }
  .maparea ul.mappoint li.tainan {
    top: 55%;
    left: 10%;
  }
}

</style>
