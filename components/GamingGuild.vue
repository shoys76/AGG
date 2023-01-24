<template>
  <div class="custom-bg w-full pt-16 pb-10 flex flex-col items-center justify-center">
    <div class="w-11/12 md:py-5">
      <p class="fadein-item text-center text-title font-bold leading-9">What is Gaming guild？</p>
    </div>
    <div class="w-11/12 flex md:flex-col flex-col-reverse md:py-14 py-3">
      <div class="">
        <p class="fadein-item font-semibold md:leading-7 md:text-base leading-5 text-sm md:px-0 px-5">
          ブロックチェーンで生成されたアイテムを貸し出し、NFTを保有していない、
          他のプレイヤー（以下、スカラー）は、それを借りてゲームプレイを
          することが可能となる制度
        </p>
      </div>
      <div class="fadein-item py-6 md:hidden px-5">
        <img src="~/assets/images/illust-mobile.png" alt="">
      </div>
      <div class="fadein-item py-12 md:block hidden px-40">
        <img src="~/assets/images/illust-pc.png" alt="">
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

.custom-bg {
  background-color: rgb(225, 225, 225);
}

</style>
