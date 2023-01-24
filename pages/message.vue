<template>
  <div class="w-full bg-white py-12">
    <div class="w-full flex flex-col justify-center items-center md:py-32 py-20">
      <div class="w-auto flex justify-end items-center md:mt-0 mt-10">
        <div class="px-9 custom-color-text md:text-lg">
          <p class="custom-color leading-7 font-semibold">
            お問合せいただき誠にありがとうございます。<br>
            返信は通常7日以内にご連絡を差し上げております。
          </p>
        </div>
      </div>
      <div class="w-full flex justify-center md:mt-20 mt-20">
        <UtilButton
          :color="'PURPLE'"
          path=""
          text="ホームへ戻る"
        />
      </div>
    </div>
  </div>
</template>

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

.custom-bg-color {
  background-color: #51418a;
}

.custom-color {
  color: #51418a;
}

.caption-text {
  font-weight: 700;
  color: #fff;
  font-size: 28px;
  padding: 0 0 10px 0; // 中心に揃えるため
  @include tab {
    font-size: 18px;
  }
}

</style>