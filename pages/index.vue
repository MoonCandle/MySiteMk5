<template>
  <div id="home">
    <div id="nav-holder">
      <nuxt-link v-for="(content, index) in pages" :key="content.page" :to="content.page" v-bind:style="{ textDecoration: 'none' }"
      ><hex :color="content.color1" :color2="content.color2" :text="content.text" :id="index"/>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
    import hex from "~/components/Hex.vue";
    export default {
        transition: {
          name: 'custom',
          mode: 'out-in',
        },
        name: "home",
        components: {
            hex
        },

        data: function() {
            return {
              pages: [
                {
                  page:`/development/`,
                  text:`Development`,
                  color1:`#2271b4`,
                  color2:`#234085`
                },
                {
                  page:`/design/`,
                  text:`Design`,
                  color1:`#1E86AC`,
                  color2:`#1d6384`
                },
                {
                  page:`/social/`,
                  text:`By Me`,
                  color1:`#1C9C9F`,
                  color2:`#197477`
                },
                {
                  page:`/about/`,
                  text:`About Me`,
                  color1:`#1FB08E`,
                  color2:`#147b64`
                }
              ]
            };
        },
        methods: {},
      mounted() {
          this.$store.commit('pages/setPage', 0)
      }
    };
</script>

<style scoped lang="scss">
  #home {
    width: 100%;
    height: 97vh;
    display: grid;
    overflow: hidden;
  }
  #nav-holder {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    width: 50%;
    height: 90px;
    align-self: center;
    justify-self: center;
    align-items: center;
    justify-items: center;
    margin-top: -10vh;
    @media (max-width: 640px) {
      align-self: start;
      margin-top: 3rem;
      grid-template-columns: 1fr;
      grid-row-gap: 5vh;
    }
  }
</style>

<style lang="scss">
  @keyframes rotate {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(359deg);
    }
  }

  @keyframes wildRotate {
    0% {
      transform: translateY(0px) translateX(0px) rotate(0deg);
      fill: #2271b4;
    }
    10% {
      transform: translateY(5px) translateX(-3px) rotate(36deg);
    }
    20% {
      transform: translateY(0px) translateX(0px) rotate(72deg);
    }
    30% {
      transform: translateY(-3px) translateX(5px) rotate(108deg);
      fill: #1e86ac;
    }
    40% {
      transform: translateY(0px) translateX(0px) rotate(144deg);
    }
    50% {
      transform: translateY(3px) translateX(2px) rotate(180deg);
    }
    60% {
      transform: translateY(0px) translateX(0px) rotate(216deg);
      fill: #1c9c9f;
    }
    70% {
      transform: translateY(-4px) translateX(-5px) rotate(252deg);
    }
    80% {
      transform: translateY(0px) translateX(0px) rotate(288deg);
    }
    90% {
      transform: translateY(4px) translateX(-2px) rotate(324deg);
      fill: #1fb08e;
    }
    100% {
      transform: translateY(0px) translateX(0px) rotate(359deg);
    }
  }

  @keyframes activeRotate {
    0% {
      transform: rotate(0deg) scale(1);
    }
    50% {
      transform: rotate(179.5deg) scale(1.4);
    }

    100% {
      transform: rotate(359deg) scale(1);
    }
  }

  @keyframes leaveRotate {
    0% {
      transform: rotate(0deg);
    }
    10% {
      transform: rotate(120deg) scale(0.7);
    }
    70% {
      transform: rotate(350deg) scale(1.1);
    }
    100% {
      transform: rotate(359deg) scale(1);
    }
  }

  @keyframes clickRotate {
    0% {
      transform: rotate(0deg) scale(1.4);
    }
    50% {
      transform: rotate(179.5deg) scale(0.7);
    }

    100% {
      transform: rotate(359deg) scale(40);
      background-color: white;
      z-index: 9999;
    }
  }

  @keyframes glow {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  @keyframes wiggle {
    0% {
      transform: translateY(0px) translateX(0px);
    }
    10% {
      transform: translateY(5px) translateX(-3px);
    }
    20% {
      transform: translateY(0px) translateX(0px);
    }
    30% {
      transform: translateY(-3px) translateX(5px);
    }
    40% {
      transform: translateY(0px) translateX(0px);
    }
    50% {
      transform: translateY(3px) translateX(2px);
    }
    60% {
      transform: translateY(0px) translateX(0px);
    }
    70% {
      transform: translateY(-4px) translateX(-5px);
    }
    80% {
      transform: translateY(0px) translateX(0px);
    }
    90% {
      transform: translateY(4px) translateX(-2px);
    }
    100% {
      transform: translateY(0px) translateX(0px);
    }
  }
  .custom-enter-active {
    animation: scale-in 0.5s;
  }

  .custom-leave-to {
    animation: fade-out forwards .8s;
  }

  @keyframes scale-in {
    0% {
      opacity: 0;
      transform: scale(0.89, 0.89);
    }
    100% {
      opacity: 1;
      transform: scale(1, 1);
    }
  }

  @keyframes fade-out {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
</style>
