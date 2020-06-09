<template>
  <section class="compare area">
    <h2>都更與危老重建差異</h2>
    <table>
      <thead>
        <tr>
          <td colspan="2">
            <img src="../assets/images/areaimg2.png" alt="都更與危老重建差異" />
          </td>
        </tr>
      </thead>
      <tbody>
        <tr data-aos="fade-down" data-aos-delay="500">
          <td>
            <span>程序冗長：3年~15年</span>
          </td>
          <td>
            <span class="winner">程序簡便：半年~2年</span>
          </td>
        </tr>
        <tr data-aos="fade-down" data-aos-delay="500">
          <td>
            <span>基地要夠大：<br />地主多，難整合被釘子戶卡死</span>
          </td>
          <td>
            <span class="winner">基地不限大小：<br />整合較簡單容易排除釘子戶</span>
          </td>
        </tr>
        <tr data-aos="fade-down" data-aos-delay="500">
          <td>
            <span>容積獎勵複雜：<br />審議會，事業計畫調查委員嚴審容積獎勵</span>
          </td>
          <td>
            <span class="winner">容積獎勵乾脆：<br />2020年前送10%最高獎勵40%</span>
          </td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script>
export default {
}
</script>

<style>
.compare table {
  margin: 1em auto;
  max-width: 100%;
}
.compare table img {
  display: block;
  margin: 0 auto;
}
.compare table thead td {
  padding: 1em 0;
}
.compare table tbody td {
  color: #4c2307;
  font-size: 1.5em;
  font-family: cwTeXFangSong;
  width: 50%;
  padding: 1em 0.6em;
}
.compare table tbody tr td:nth-child(2) span {
  position: relative;
  display: inline-block;
}

@media screen and (min-width: 481px) {
  .compare table tbody tr.aos-animate span.winner:after {
    content: '';
    position: absolute;
    width: 60px;
    height: 60px;
    top: 0;
    right: 0;
    transform: translate(90%, -40%) scale(0);
    background-image: url('../assets/images/win.png');
    background-size: cover;
    animation: radialIn 0.5s;
    animation-fill-mode: forwards;
    animation-delay: 1s;
  }
}

@media screen and (max-width: 768px) {
  .compare table tbody td {
    font-size: 1.3em;
  }
  .compare table tbody tr.aos-animate span.winner:after {
    width: 40px;
    height: 40px;
  }
  .compare table img {
    width: 74%;
  }
}

@media screen and (max-width: 550px) {
  .compare {
    overflow: hidden;
  }
}

@media screen and (max-width: 480px) {
  .compare table tbody td {
    font-size: 1.1em;
    padding: 0.5em 0;
  }
  .compare table tbody tr.aos-animate span.winner:after {
    content: '';
    position: absolute;
    width: 30px;
    height: 30px;
    bottom: 0;
    right: 0;
    transform: translate(5%, 70%) scale(0);
    background-image: url('../assets/images/win.png');
    background-size: cover;
    animation: radialInMobile 0.5s;
    animation-fill-mode: forwards;
    animation-delay: 1s;
  }
  .compare table img {
    width: 100%;
  }
}

@keyframes radialIn {
  from {
    transform: translate(90%, -40%) scale(0);
  }
  75% {
    transform: translate(90%, -40%) scale(1.2);
  }
  to {
    transform: translate(90%, -40%) scale(1);
  }
}

@keyframes radialInMobile {
  from {
    transform: translate(5%, 70%) scale(0);
  }
  75% {
    transform: translate(5%, 70%) scale(1.2);
  }
  to {
    transform: translate(5%, 70%) scale(1);
  }
}

</style>
