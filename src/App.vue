<template>
  
  
  <!-- <img alt="Vue logo" src="./assets/logo.png" style="width:100px; height: 40px;"> -->
  <!-- <nav>
    <ul>
      <li><a>홈</a></li>
      <li><a>상품</a></li>
      <li><a>장바구니</a></li>
    </ul>
  </nav> -->
  <NaviCom/>
  <!-- 모달 -->

  <div  class="modalOuterBg" v-if="modalFlag">
      <button class="modalBtn" @click="modalFlag = false">X</button>
      <div class="modalInnerBg">
        <img :src="products[proNum].img" alt="" style="width:300px; height: 180px;">
        <h4>상품명 : <span>{{ products[proNum].name }}</span></h4>
        <p>가격 : <span>{{ products[proNum].price }}</span></p>
        <p>{{ products[proNum].contents }}</p>
        <p>count : <span>{{ products[proNum].count }}</span></p>
        <p>total price : <span>{{ products[proNum].price * products[proNum].count }}</span></p>
      </div>
    </div>
  

  <!-- 상품 -->
  <div v-for="(item, i) in products" :key="i" >
    <!-- <img src="./assets/pro'{{ i }}.png" alt=""> -->
    <img :src="item.img" alt="" style="width:300px; height: 180px;">
    <h4 @click="open(i)">{{ item.name }}</h4>
    <p>{{ item.price }}</p>
    <button v-on:click="add(i)">+</button>
        <button v-if="item.count <= 0" type="button">-</button>
        <button v-else-if="item.count > 0" v-on:click="remove(i)">-</button>
        <p>count : <span>{{ item.count }}</span></p>
        <p>total price : <span>{{ item.price * item.count }}</span></p>
  </div>
  <!-- if문 -->
  <!-- <p v-if="1 == 2">if문 테스트 1 == 2</p>
  <p v-if="1 == 1">if문 테스트 1 == 1</p> -->

  <!-- 이벤트핸들러 -->

</template>

<script>
  import data from './assets/js/data.js'
import navi from './components/NaviCom.vue';

  export default {
  components: { navi },
  name: 'App',
  data() {
    return {
      products: data,
      modalFlag: false,
    }
  },
  methods: {
    add(i) {
      this.proNum = i;
      this.products[i].count++;
      this.count++
    },
    remove(i) {
      this.proNum = i;
      this.products[i].count--;
      this.count--
    },
    open(i){
      this.modalFlag = true;
      this.proNum = i;
    },
  },
}
</script>

<style>
@import url('./assets/css/style.css');
*{background-color: antiquewhite; box-sizing: border-box;}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
  margin-top: 60px;
}

nav {
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

ul {
    list-style: none;
    background: #003754;
    width: 100%;
    padding: 10px 25px;
    display: flex;
  align-items: center;
  justify-content: space-around;
}

li:hover {background: #ef4ca6;}

/* li {
    float: left;
} */

a {
    background: #003754;
    color: #FFFFFF;
    padding: 10px 25px;
    text-align: center;
    text-decoration: none;
}

li a:hover {background: #ef4ca6;}
</style>
