<template>
  <div class="sop area">
    <h2>完全圖解><mark>申請危老最速上手SOP</mark></h2>
    <p>危老申請過程中包括初評、找建築師規畫、拆屋興建後在外租屋、營造費用，每個環節都要花錢，最常見的狀況是「有房子的人，不見得有錢」。</p>
    <p>「愈了解法規，愈可以節省申請時間與營建費用，也可以早日住進新屋。」相較都更冗長的申請過程，危老的低門檻替很多屋主圓了重建的夢想，掌握眉角就不會白走冤枉路。</p>
    <ul>
      <li data-aos="fade-down" data-aos-once="true" data-aos-id="sop">
        <div>
          <div class="title"><h4 data-index="1">自宅調查</h4></div>
          <dl>
            <dt>是否位於都市計畫區內 (可上營建署網站查詢)</dt>
            <dt>是否為合法建築物</dt>
            <dt>是否為「不具歷史文化保存價值」 (可向各縣市文化局查詢)</dt>
            <dt>屋齡是否超過30年</dt>
          </dl>
        </div>
      </li>
      <li :class="setAnimate(2)">
        <div>
          <div class="title"><h4 data-index="2">首次揪團</h4></div>
          <p>為了申請安全評估，你必須取得：</p>
          <dl>
            <dt>5成以上建築物所有權人同意</dt>
            <span>或是</span>
            <dt>公寓大廈區分所有權人會議決議通過</dt>
          </dl>
        </div>
      </li>
      <li :class="setAnimate(3)">
        <div>
          <div class="title"><h4 data-index="3">申請初評</h4></div>
          <p>找評估機構 (可上營建署「危老重建專區」尋找)。經評估，耐震等級為「乙級或乙級以下」才能申請危老重建。</p>
        </div>
      </li>
      <li :class="setAnimate(4)">
        <div>
          <div class="title"><h4 data-index="4">再次揪團</h4></div>
          <p>申請危老重建前，必須取得全體土地及建築物所有權人同意。</p>
        </div>
      </li>
      <li :class="setAnimate(5)">
        <div>
          <div class="title"><h4 data-index="5">找建築師</h4></div>
          <p>請建築師評估基地進行危老重建的可行性、建物規畫，並擬寫「重建計畫書」。</p>
        </div>
      </li>
      <li :class="setAnimate(6)">
        <div>
          <div class="title"><h4 data-index="6">籌備資金</h4></div>
          <p>若需要銀行貸款，上一階段的「重建計畫書」最好能加入「還款計畫」；核貸金額通常為總成本的7成。</p>
        </div>
      </li>
      <li :class="setAnimate(7)">
        <div>
          <div class="title"><h4 data-index="7">申請建照</h4></div>
          <p>重建計畫書審核過關，重建房屋的資金也搞定之後，即可申請建造執照。</p>
        </div>
      </li>
      <li :class="setAnimate(8)">
        <div>
          <div class="title"><h4 data-index="8">找營造廠</h4></div>
          <p>這部分，推動師、建築師或其他提供一條龍服務的整合公司等，通常都有合作管道。</p>
        </div>
      </li>
    </ul>
    <div class="readmore">
      <a href="#" target="_blank">看完整文章</a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      animateIndex: 1
    }
  },
  methods: {
    setAnimate(index) {
      return this.animateIndex >= index ? 'slidein' : ''
    },
    runAnimate() {
      const intervalAnimate = setInterval(() => {
        if(this.animateIndex >= 8) {
          clearInterval(intervalAnimate);
          document.removeEventListener('aos:in:sop', this.runAnimate);
        } else {
          this.animateIndex++;
        }
      }, 500)
    }
  },
  mounted() {
    document.addEventListener('aos:in:sop', this.runAnimate);
  }
}
</script>

<style>
.sop ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.sop ul li {
  opacity: 0;
  position: relative;
  width: 30%;
  margin: 80px 10%;
  background: #b7d8da;
  border-radius: 15px;
  padding: 5px;
}
.sop ul li.slidein {
  animation-duration: .5s;
  animation-fill-mode: both;
  animation-name: slideInDown;
}
.sop ul li:after {
  content: '';
  width: 100px;
  height: 52px;
  background-image: url('../assets/images/arrow.png');
  background-size: cover;
  position: absolute;
}
.sop ul li:last-child:after {
  display: none;
}
.sop ul li:nth-child(1):after,
.sop ul li:nth-child(5):after
{
  top: 50%;
  right: -33.3333%;
  transform: translate(50%, -50%);
}
.sop ul li:nth-child(3):after,
.sop ul li:nth-child(7):after
{
  top: 50%;
  left: -33.3333%;
  transform: translate(-50%, -50%) rotate(180deg);
}
.sop ul li:nth-child(2):after,
.sop ul li:nth-child(4):after,
.sop ul li:nth-child(6):after
{
  left: 50%;
  bottom: -80px;
  transform: translate(-50%, 25px) rotate(90deg);
}
.sop ul li:nth-child(1) {
  order: 1;
}
.sop ul li:nth-child(2) {
  order: 2;
}
.sop ul li:nth-child(3) {
  order: 4;
}
.sop ul li:nth-child(4) {
  order: 3;
}
.sop ul li:nth-child(5) {
  order: 5;
}
.sop ul li:nth-child(6) {
  order: 6;
}
.sop ul li:nth-child(7) {
  order: 8;
}
.sop ul li:nth-child(8) {
  order: 7;
}
.sop ul li > div {
  height: 100%;
  padding: 0.5em 1em;
  padding-left: 2em;
  border-radius: 10px;
  background: linear-gradient(to top, rgba(255, 255, 255, 1) 0%, rgba(255, 255, 255, 0) 100%);
}
.sop ul li .title {
  display: flex;
  align-items: baseline;
}
.sop ul li .title:after {
  content: '';
  flex: 1;
  height: 3px;
  background-image: url('../assets/images/dotted.svg');
  background-repeat: repeat-x;
  margin-left: 0.2em;
}
.sop ul li .title h4 {
  position: relative;
  font-size: 1.4em;
  color: #4e75ab;
  margin: 0;
}
.sop ul li .title h4:before {
  content: attr(data-index) '. ';
  position: absolute;
  transform: translate(-100%, 0);
  color: white;
}
.sop dl {
  padding-left: 1.5em;
}
.sop dt {
  position: relative;
}
.sop dt:before {
  content: '';
  position: absolute;
  transform: translate(-100%, 0);
  height: 0.5em;
  width: 0.5em;
  border: solid 1px;
  left: -0.5em;
  top: 0.4em;
}

@media screen and (max-width: 1360px) {
  .sop ul li {
    width: 40%;
    margin: 60px 5%;
  }
  .sop ul li:after {
    width: 60px;
    height: 31px;
  }
  .sop ul li:nth-child(1):after,
  .sop ul li:nth-child(5):after
  {
    right: -12.5%;
  }
  .sop ul li:nth-child(3):after,
  .sop ul li:nth-child(7):after
  {
    left: -12.5%;
  }
  .sop ul li:nth-child(2):after,
  .sop ul li:nth-child(4):after,
  .sop ul li:nth-child(6):after
  {
    bottom: -60px;
    transform: translate(-50%, 20px) rotate(90deg);
  }
}

@media screen and (max-width: 768px) {
  .sop ul li {
    width: 42%;
    margin: 60px 0;
  }
  .sop ul li:nth-child(1):after,
  .sop ul li:nth-child(5):after
  {
    right: -20%;
  }
  .sop ul li:nth-child(3):after,
  .sop ul li:nth-child(7):after
  {
    left: -20%;
  }
  .sop ul li .title h4 {
    font-size: 1.3em;
  }
}

@media screen and (max-width: 600px) {
  .sop ul {
    display: block;
  }
  .sop ul li {
    width: 100%;
    margin: 50px 0;
  }
  .sop ul li:nth-child(odd):after,
  .sop ul li:nth-child(even):after
  {
    left: 50%;
    right: auto;
    top: auto;
    bottom: 0;
    transform: translate(-50%, 30px) rotate(90deg);
  }
  .sop ul li:last-child {
    margin-bottom: 1em;
  }
  .sop ul li .title h4 {
    font-size: 1.2em;
  }
  .sop ul li p {
    margin-top: 0.5em;
  }
}

@media screen and (max-width: 320px) {
  .sop ul li > div {
    padding: 0.3em 0.6em;
    padding-left: 1.6em;
  }
  .sop dl {
    padding-left: 1em;
  }
}

</style>
