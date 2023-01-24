<template>
  <div class="bg-custom w-full py-16 flex flex-col items-center justify-center">
    <div class="w-11/12 mb-10">
      <p class="fadein-item text-center text-title font-bold text-white">News</p>
    </div>
    <div class="w-full flex justify-center items-center">
      <div class="fadein-item bg-white md:w-7/12 w-11/12 rounded-xl pt-8 pb-3 md:px-6 px-2">
        <!-- 9行目のタグをUtilNewsを追加することでNewsを更新できる -->
        <UtilNews text="プレスリリースを公開しました" date="2023.01.27" type="News" />
        <!--
            下記の文言を入れ替えてコメントを外すことによってページにニュースを追加することができる
              text: ニュースの文言
                例) プレスリリースを公開しました, サイトをリニューアルしました...
              date: 日付を入れる
              type: アナウンスの種類を入れる
                例) News, Announce...
        -->
        <!-- <UtilNews text="プレスリリースを公開しました" date="2023.01.27" type="News" /> -->
        <!-- <UtilNews text="プレスリリースを公開しました" date="2023.01.27" type="News" /> -->
        <!-- <UtilNews text="プレスリリースを公開しました" date="2023.01.27" type="News" /> -->
        <!-- <UtilNews text="プレスリリースを公開しました" date="2023.01.27" type="News" /> -->
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
  background:
    linear-gradient(to top,rgba(177, 153, 48, 0.7) 40%, rgba(227, 216, 174, 0.7) 100%),
    url('~/assets/images/top/menya_dragon_ramen.png');
  background-size: cover;
  background-position: left 80px top 0px, center;
}

</style>