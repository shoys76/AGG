<template>
  <div class="w-full py-16 flex flex-col items-center justify-center">
    <div class="w-11/12">
      <p class="fadein-item text-center text-title font-bold">Games</p>
    </div>
    <div class="fadein-item w-10/12 md:flex md:flex-wrap hidden">
      <div class="w-2/12" v-for="(game, index) in gameUrls" :key="index">
        <div class="h-52 px-3 flex justify-center items-center">
          <div class="p-2 bg-white custom-shadow rounded-xl cursor-pointer" @click="openExternalLink(game.url)">
            <img class="inline-block" :src="game.path" alt="">
          </div>
        </div>
      </div>
    </div>
    <div class="fadein-item w-full flex justify-center py-14 md:hidden ">
      <carousel
        :per-page="2"
        :navigation-enabled="false"
        :pagination-enabled="true"
        :scroll-per-page="true"
        :speed="1000"
        pagination-active-color="#b19930"
        pagination-color="#333333"
        :loop="true"
      >
        <slide v-for="(game, index) in gameUrls" :key="index">
          <div class="h-52 px-3 flex justify-center items-center">
            <div class="p-2 bg-white custom-shadow rounded-xl" @click="openExternalLink(game.url)">
              <img class="inline-block" :src="game.path" alt="">
            </div>
          </div>
        </slide>
      </carousel>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel'

export default ({
  components: {
    Carousel,
    Slide,
  },
  data () {
    return {
      gameUrls: [
        {
          path: require('~/assets/images/games/cookin_burger.png'),
          url: 'https://www.cookinburger.com/ja/'
        },
        {
          path: require('~/assets/images/games/graffiti_racer.png'),
          url: 'https://graffitiracer.playmining.com/'
        },
        {
          path: require('~/assets/images/games/job_tribes.png'),
          url: 'https://jobtribes.playmining.com/'
        },
        {
          path: require('~/assets/images/games/lucky_farmer.png'),
          url: 'https://luckyfarmer.playmining.com/'
        },
        {
          path: require('~/assets/images/games/menya_dragon_ramen.png'),
          url: 'https://dragonramen.flypenguin-games.com/'
        },
        {
          path: require('~/assets/images/games/play_mining.png'),
          url: 'https://playmining.com/'
        },
      ],
      elements: null
    }
  },
  mounted () {
    this.elements = document.querySelectorAll(".fadein-item");
    window.addEventListener('scroll', this.fadeIn);
  },
  computed: {
  },
  methods: {
    fadeIn () {
      for (var i = 0; i < this.elements.length; i++) {
        const elem = this.elements[i]
        var distInView = elem.getBoundingClientRect().top - window.innerHeight + 20;
        if (distInView < 0) {
          elem.classList.add("inView");
        } else {
          elem.classList.remove("inView");
        }
      }
    },
    openExternalLink (url) {
      window.open(url, '_blank')
    }
  }
})
</script>

<style lang="scss" scoped>
@mixin pcM {
  @media (max-width: ($pcM)) { @content; }
}
@mixin tab {
  @media (max-width: ($tab)) { @content; }
}
@mixin sp {
  @media (max-width: ($sp)) { @content; }
}
.text-title {
  font-size: 40px;
  @include sp {
    font-size: 22px;
  }
}

.custom-shadow {
  box-shadow: 0 8px 13px rgba(0,0,0,0.30), 0 5px 5px rgba(0,0,0,0.1);
}

</style>