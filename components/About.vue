<template>
  <div class="w-full py-16 flex items-center justify-center bg-custom">
    <div class="w-10/12 flex md:flex-row flex-col">
      <div class="w-full md:block flex md:flex-row flex-col">
        <div class="w-full mb-7 md:pb-8 pb-5">
          <p class="fadein-item text-title font-bold text-center text-white leading-9">What is <br class="md:hidden">Academy Guild Games?</p>
        </div>
        <div class="md:flex block">
          <div class="md:w-4/12">
            <img class="fadein-item" src="~/assets/images/about.png" alt="">
          </div>
          <div class="fadein-item md:w-8/12 md:text-lg font-semibold md:mt-0 mt-12 md:px-10 text-white md:leading-7 md:text-base leading-5 text-sm">
            <p class="text-lg">ゲーミングギルド「Academy Guild Games(AGG)」は、先進的なNFTゲームを体験し、新しいインターネットの扉が開く瞬間を体感いただけます。</p>
            <p class="text-sm pt-5">
              Academy Guild Games (AGG) は日本の未来を担ってゆく学生達に、「Game-Fi」を通じて「NFT」「Crypto」「Web3.0」を肌で感じ、体験してもらい「世界に通用する人材の育成」をMissionに立ち上がりました。
            </p>
            <p class="text-sm py-3">
              ゲームギルドは国内に複数社存在しますがスカラー（ゲームプレイヤー）を日本人の学生の方々に焦点を当てているギルドは当ギルドのみとなっております。
            </p>
            <p class="text-sm">
              昨今様々な経済圏で遅れをとっている日本が唯一世界をリードしているものがゲームやアニメ業界だと我々は考えています。
              日本の若き学生達にいち早くweb3.0を体験して頂き、今後加速するクリプト市場の先陣を切っていくような人材が生まれるギルドを作るべく活動して参ります。
            </p>
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
    window.addEventListener('scroll', this.fadeIn);
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

.bg-custom {
  background-color: #b19930;
}

</style>
