<template>
  <div class="w-full h-screen md:pt-16 relative">
    <!-- PC -->
    <div class="hidden md:flex h-full">
      <div class="w-4/12 flex items-center z-10">
        <div class=" pl-20">
          <div>
            <img class="fadein-item w-72" src="~/assets/images/top/agg-logo-1.png" alt="">
          </div>
          <div class="fadein-item text-lg mt-4 font-semibold">Academy Guild Games</div>
          <div class="fadein-item whitespace-nowrap title-text mt-3 mb-5">国内初の学生型ゲーミングギルド</div>
          <div class="fadein-item font-bold text-lg">NFTゲームをプレイして、仮想通貨を増やそう！</div>
          <div class="flex items-center">
            <div class="fadein-item button-section relative rounded-full mt-5">
              <div class="button-section__image">
                <img src="~/assets/images/top/discord-icon.svg" alt="">
              </div>
              <button class="button-section__button text-white font-semibold text-2xl pl-5" @click="openDiscordLink">JOIN</button>
            </div>
          </div>
        </div>
      </div>
      <div class="w-8/12 flex items-center">
        <div class="z-0">
          <img class="fadein-item z-0" src="~/assets/images/top/top-pc.png" alt="">
        </div>
      </div>
    </div>
    <!-- mobile -->
    <div class="md:hidden h-screen relative flex items-center justify-center">
      <div class="fadein-item h-full absolute top-0 w-full">
        <div class="h-full main-bg-container pt-14"><img class="main-bg" src="~/assets/images/top/main-bg-v2.png" alt=""></div>
      </div>
      <div class="fadein-item custom-box bg-white rounded-full bg-opacity-80 z-10 flex flex-col items-center">
        <div class="flex flex-col items-center mt-7 mb-4">
          <img class="w-24" src="~/assets/images/top/agg-logo-2.svg" alt="">
          <div class="fadein-item text-sm mt-1 text-center font-semibold">Academy Guild Games</div>
        </div>
        <div class="font-bold text-3xl text-center">国内初の学生型<br>ゲーミングギルド</div>
        <div class="text-sm font-bold mt-2 mb-8 text-center">NFTゲームをプレイして、<br>仮想通貨を増やそう！</div>
        <div class="flex items-center justify-center">
          <div class="relative button-section rounded-full">
            <div class="button-section__image">
              <img src="~/assets/images/top/discord-icon.svg" alt="">
            </div>
            <button class="button-section__button text-white font-semibold text-2xl pl-5" @click="openDiscordLink">JOIN</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default ({
  data () {
    return {
      elements: null
    }
  },
  mounted () {
    this.elements = document.querySelectorAll(".fadein-item");
    this.fadeIn()
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
    openDiscordLink () {
      window.open('https://discord.gg/4AHy4u8xbd', '_blank')
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

.title-text {
  font-size: 40px;
  font-weight: 700;
}

.main-bg {
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.main-bg-container {
  width: 100%;
}


.button-section {
  background: linear-gradient(to right, #b6bfe1, #4C5FAA);
  display: flex;
  position: relative;
  width: 180px;
  transition-duration: 0.4s;/*変化の時間*/
  cursor: pointer;
  &:hover {
    transform: translateY(-6px);
    box-shadow: 0px 8px 18px -5px rgba(85, 85, 85, 0.75);
  }
  &__image {
    position: relative;
    img {
      width: 60px;
    }
  }
  &__button {}
}

.custom-box {
  height: 350px;
  width: 350px;
}

</style>
