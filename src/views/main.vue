<template lang="pug">
  .main-wrapper
    vi-header
    .content-wrapper
      modules
      div(v-if="load")
        headline
        board
        super_sale
        shop_list
      .loading(v-else)
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import { State, Action, Getter } from "vuex-class";
import header from "@/components/header.vue";
import modules from "@/components/modules.vue";
import headline from "@/components/headline.vue";
import board from "@/components/board.vue";
import super_sale from "@/components/super_sale.vue";
import shop_list from "@/components/shops.vue";

@Component({
  components: {
    "vi-header": header,
    modules,
    headline,
    board,
    super_sale,
    shop_list
  }
})
export default class App extends Vue {
  @State login: boolean;
  @Action initAjax: () => void;
  @Getter load: boolean;

  get isLogin(): boolean {
    return this.login;
  }

  mounted() {
    this.initAjax();
  }
}
</script>

<style lang="stylus">
.content-wrapper {
  padding-top: 50px;
}

.loading {
  background: url('//www.dpfile.com/app/app-m-module/static/6261145dd7c0f26bc0a26831e5cb358a.gif') center 30px no-repeat #fff;
  background-size: 90px;
  height: 300px;
}
</style>
