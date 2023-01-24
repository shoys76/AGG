<template>
  <div class="bg-custom w-full md:py-24 py-16 flex flex-col items-center justify-center">
    <div class="w-11/12 mb-10">
      <p class="fadein-item text-center text-title font-bold text-white">Contact</p>
    </div>
    <div class="w-full flex justify-center items-center">
      <div class="fadein-item bg-white md:w-7/12 w-11/12 h-56 rounded-xl pt-8 pb-3 md:px-6 px-2">
        <div class="flex flex-col items-center md:flex-row md:block">
          <div class="text-gray-700 md:text-2xl text-lg mb-3 font-semibold">お問合せ</div>
          <div class="mb-3">
            <p class="text-gray-700 text-sm">お問合せページはこちら</p>
          </div>
          <div class="py-5">
            <UtilButton
              :color="'YELLOW'"
              path="contact"
              type="PATH"
              text="Contact"
            />
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

.color-custom {
  color: #b19930;
}

.bg-custom {
  background:
    linear-gradient(to top,rgba(177, 153, 48, 0.7) 40%, rgba(227, 216, 174, 0.7) 100%),
    url('~/assets/images/top/job_tribes.png');
  background-size: cover;
  background-position: left 80px top 0px, center;
}

</style>