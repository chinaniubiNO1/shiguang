<template>
  <div class="shop shopWrapper" ref="shopWrapper">
    <Header></Header>
    <div>
      <Input></Input>
      <Banner></Banner>
      <List></List>
      <Cell></Cell>
      <Topic></Topic>
    </div>
  </div>
</template>
<script>
import Vuex from "vuex";
import Header from "../common/header";
import Input from "./components/input";
import Banner from "./components/banner";
import List from "./components/list";
import Cell from "./components/cell";
import Topic from "./components/topic";
import BScroll from "better-scroll";

export default {
  components: {
    Header: Header,
    Input: Input,
    Banner: Banner,
    List: List,
    Cell: Cell,
    Topic: Topic
  },
  created() {
    this.handleShopDate();
  },
  computed: {
    ...Vuex.mapState({
      state: state => state.shop,
      banners: state => state.shop.scrollImg,
      navigatorIcon: state => state.shop.navigatorIcon,
      cellA: state => state.shop.cellA,
      cellB: state => state.shop.cellB,
      cellC: state => state.shop.cellC,
      topic: state => state.shop.topic
    })
  },
  methods: {
    ...Vuex.mapActions({
      handleShopDate: "shop/handleShopDate"
    }),

    ...Vuex.mapMutations({
      handleShopData: "shop/handleShopData"
    })
  },
  mounted () {
     this.scroll = new BScroll(this.$refs.shopWrapper,{
       click:true,
       scrollY:true,
       tap:true
     });
     console.log(this.scroll)
  }   
}


</script>

<style  scoped>
.shop {
  height: 100%;
  width: 100%;
}


</style>