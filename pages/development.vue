<template>
  <div class="dev">
    <display-page :content="DevContent" :WhatPage="'development'"></display-page>
  </div>
</template>

<script>
import DisplayPage from "@/components/DisplayPage.vue";
import Img from "../content/bio/bioImg";
export default {
    transition: {
        name: 'custom',
        mode: 'out-in',
    },
  data() {
    return{
      DevContent: [
        {
          title: `Css Grid Framework`,
          img: `grid.svg`,
        },
        {
          title: `Modular Form Component`,
          img: `form.svg`
        }
      ]
    }
  },
  components: {
    Img,
    DisplayPage
  },
  mounted() {
    this.$store.commit('pages/setPage', 1)
  }
};
</script>

<style lang="scss">


</style>
