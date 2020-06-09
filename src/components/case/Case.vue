<template>
  <div class="case area">
    <h2>三個經典案例，看懂危老如何解決都更痛點</h2>
    <ul>
      <CaseList
        v-for="list in caselist"
        :key="list.index"
        :caselist="list"
        :isMobile="isMobile"
        data-aos="fade"
      />
    </ul>
  </div>
</template>

<script>
import CaseList from './CaseLise'
import image1 from '../../assets/images/case1.jpg'
import image2 from '../../assets/images/case2.jpg'
import image3 from '../../assets/images/case3.jpg'

export default {
  components: {
    CaseList,
  },
  props: {
    isMobile: {
      type: Boolean,
      requiredtrue: true
    }
  },
  data() {
    return {
      caselist: [
        {
          title: '速度最快',
          article: '危老重建號稱『都更的高速公路』，標榜申請程序簡便，以新北市板橋『欣璞綻』為例，送件申請到核准，含例假日僅僅12天。',
          image: image1
        },
        {
          title: '整合簡單',
          article: '由於危老重建沒有地基大小的限制，地主整合相對簡單，以台北市遼寧街興建中的『紙片屋』為例，左鄰右舍整合不易，屋主獨自申請過關。',
          image: image2
        },
        {
          title: '獎勵乾脆',
          article: '危老重建的容積獎勵規定明確，屋主更能掌握訣竅爭取獎勵，新北市板橋太和街的案例中，屋主能夠百坪換百坪。',
          image: image3
        }
      ]
    }
  }
}
</script>
