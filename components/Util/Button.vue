<template>
  <button
    v-if="type === 'SUBMIT'"
    :disabled="disabled"
    type="submit"
    class="button"
    :class="{
      'bg-main-purple': color === 'PURPLE',
      'bg-main-yellow': color === 'YELLOW',
      'disabled': disabled,
      'enabled': !disabled
      }"
    >
    <div class="button__text">
      {{ text }}
    </div>
    <div class="button__icon">
      <img v-if="color === 'YELLOW'" src="~/assets/images/nav-white.svg" alt="">
      <img v-if="color === 'PURPLE'" src="~/assets/images/nav-white.svg" alt="">
    </div>
  </button>
  <button
    v-else
    :disabled="disabled"
    type="button"
    class="button"
    :class="{
      'bg-main-purple': color === 'PURPLE',
      'bg-main-yellow': color === 'YELLOW',
      'disabled': disabled,
      'enabled': !disabled
      }"
    @click="openPage(path)"
  >
    <div class="button__text">
      {{ text }}
    </div>
    <div class="button__icon">
      <img v-if="color === 'YELLOW'" src="~/assets/images/nav-white.svg" alt="">
      <img v-if="color === 'PURPLE'" src="~/assets/images/nav-white.svg" alt="">
    </div>
  </button>
</template>

<script>
export default ({
  props: {
    text: {
      type: String,
      default: null
    },
    color: {
      type: String,
      default: null
    },
    path: {
      type: String,
      default: null
    },
    type: {
      type: String,
      default: null
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    openPage (path) {
      console.log(path)
      const url = `/${path}`
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
.bg-main-purple {
  background: #321b83;
  -moz-box-shadow: 8px 8px 3px 1px #d9d9da;
  -webkit-box-shadow: 8px 8px 3px 1px #d9d9da;
  -ms-box-shadow: 8px 8px 3px 1px #d9d9da;
  box-shadow: 8px 8px 3px 1px #d9d9da;
}
.bg-main-yellow {
  background: #b19930;
  -moz-box-shadow: 8px 8px 3px 1px #d9d9da;
  -webkit-box-shadow: 8px 8px 3px 1px #d9d9da;
  -ms-box-shadow: 8px 8px 3px 1px #d9d9da;
  box-shadow: 8px 8px 3px 1px #d9d9da;
}
.disabled { opacity: .6; }
.enabled {
  &:hover {
    opacity: .8;
  }
}
.button {
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 15px 75px;
  border-radius: 50px;
  @include sp {
    padding: 10px 60px;
  }
  &__text {
    padding-top: 2px;
    line-height: 20px;
    font-weight: 600;
    font-size: 14px;
    color: #fff;
    @include sp {
      font-size: 16px;
    }
  }
  &__icon {
    position: absolute;
    right: 40px;
    @include sp {
      right: 30px;
    }
    img{
      height: 16px;
      width: 16px;
    }
  }
}
</style>