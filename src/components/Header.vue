<template>
  <header>
    <div class="wrapper">
      <a class="businesstoday" href="https://www.businesstoday.com.tw/" target="_blank">
        <img src="../assets/images/businesstoday.svg" alt="今周刊" />
      </a>
      <ul>
        <li><a href="#" target="_blank"><i class="fab fa-facebook-square" /></a></li>
        <li><a href="#" target="_blank"><i class="fab fa-line" /></a></li>
        <li><a href="#" target="_blank"><i class="fab fa-instagram" /></a></li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style>
header {
  position: fixed;
  display: flex;
  align-items: center;
  width: 100%;
  height: 60px;
  background: #ffc000;
  z-index: 99;
}
header .wrapper {
  display: flex;
  align-items: center;
}
header .businesstoday img {
  width: 100px;
  display: inline-block;
}
header ul {
  display: flex;
  flex: 1;
  justify-content: flex-end;
  align-items: center;
}
header ul li {
  display: inline-block;
  margin: 0 0.5em;
}
header ul li i {
  color: white;
  font-size: 40px;
}
header img,
header i
{
  opacity: 1;
  transition: .5s;
}

@media (hover: hover) {
  header img:hover,
  header i:hover
  {
    opacity: .6;
  }
}

@media screen and (max-width: 480px) {
  header {
    height: 50px;
  }
  header .businesstoday img {
    width: 80px;
  }
  header ul li {
    margin: 0;
  }
  header ul li i {
    font-size: 35px;
    padding: 5px 8px;
  }
}

</style>
