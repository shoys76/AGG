<template>
  <div class="w-full bg-white py-12">
    <div class="custom-bg-color md:py-28 py-16 md:mb-6 mb-3 relative flex items-center justify-center">
      <div class="caption-text">お問い合わせ</div>
    </div>
    <div class="w-full flex justify-center">
      <div class="fadein-item md:w-5/12 w-full md:mt-20 mt-16 md:px-0 px-8">
        <form
          action="https://docs.google.com/forms/u/0/d/e/1FAIpQLScrHKU1AHg3U6YyFbEajwB6RFgBctupgQdUF3jsXndUqilWEg/formResponse"
          method="post"
          id="google-form"
          @submit.prevent="submit"
        >
          <div class="mb-3 flex flex-col">
            <label class="mb-1 text-base" for="name">お名前</label>
            <input v-model="form.name" class="h-10 text-base" type="text" name="entry.1373584852" id="name" required>
          </div>
          <div class="mb-3 flex flex-col">
            <label class="mb-1 text-base" for="phone">電話番号</label>
            <input v-model="form.phone" class="h-10 text-base" type="number" name="entry.1345986294" id="phone">
            <span class="small-caption">※番号のみ</span>
          </div>
          <div class="mb-3 flex flex-col">
            <label class="mb-1 text-base" for="email">メールアドレス</label>
            <input v-model="form.email" class="h-10 text-base" type="email" name="entry.2095080596" id="email" required>
          </div>
          <div class="mb-3 flex flex-col">
            <label class="mb-1 text-base" for="phone">ご希望の返信方法</label>
            <div class="custom-radio">
              <input type="radio" id="replyByEmail" value="メール" name="entry.435093788" v-model="form.replyMethod">
              <label for="replyByEmail">メール</label>
            </div>
            <div class="custom-radio">
              <input type="radio" id="replyByPhone" value="電話" name="entry.435093788" v-model="form.replyMethod">
              <label for="replyByPhone">電話</label>
            </div>
            <div class="custom-radio">
              <input type="radio" id="replyByAny" value="どちらでも可" name="entry.435093788" v-model="form.replyMethod">
              <label for="replyByAny">どちらでも可</label>
            </div>
          </div>
          <div class="mb-3 flex flex-col">
            <label class="mb-1 text-base" for="content">お問い合わせ内容</label>
            <textarea v-model="form.content" class="md:h-56 h-44 p-3" type="text" name="entry.500021243" id="content" required />
          </div>
          <div class="w-full flex justify-center md:mt-20 mt-10">
            <UtilButton
              :color="'PURPLE'"
              :disabled="!form.name || !form.phone || !form.email || !form.replyMethod || !form.content"
              type="SUBMIT"
              text="送信する"
            />
          </div>
        </form>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios'
export default {
  data() {
    return {
      elements: null,
      form : {
        name: '',
        phone: '',
        email: '',
        replyMethod: null,
        content: ''
      },
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
    async submit () {
      try {
        const submitParams = new FormData()
        submitParams.append('entry.1373584852', this.form.name);
        submitParams.append('entry.1345986294', this.form.phone);
        submitParams.append('entry.2095080596', this.form.email);
        submitParams.append('entry.435093788', this.form.replyMethod);
        submitParams.append('entry.500021243', this.form.content);
        const GOOGLE_FORM_ACTION = 'https://docs.google.com/forms/u/0/d/e/1FAIpQLScrHKU1AHg3U6YyFbEajwB6RFgBctupgQdUF3jsXndUqilWEg/formResponse'
        await axios.post(GOOGLE_FORM_ACTION, submitParams)
      } catch (e) {
        console.log(e)
      } finally {
        window.location.href = '/message'
      }
    }
  }
}
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
.custom-button {
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 15px 75px;
  border-radius: 50px;
  @include sp {
    padding: 10px 60px;
  }
}

.custom-bg-color {
  background-color: #51418a;
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

.small-caption {
  margin-top: 5px;
  color: #51418a;
  font-size: 12px;
}

label {
  color: #321b83;
  font-weight: 600;
}

input[type="text"], input[type="number"], input[type="email"], textarea {
  border: 1px solid #321b83;
  padding: 2px 3px;
  color: rgb(63, 63, 63);
}

/* radio */
.custom-radio {
  margin: 10px 0;
  display: flex;
  align-items: center;
}

.custom-radio input[type="radio"]{
    display: none;
}

.custom-radio input[type="radio"]{
    display: none;
    cursor: pointer;
    display: inline-block;
    position: relative;
    padding-left: 25px;
    padding-right: 10px;
}

.custom-radio input[type="radio"]::before{
    border-radius: 30%;
    content: "";
    position: absolute;
    display: block;
    box-sizing: border-box;
    width: 20px;
    height: 20px;
    margin-top: -10px;
    left: 0;
    top: 50%;
    border: 2px solid;
    border-color:  #321b83;
    background-color: #fff;
}

.custom-radio input[type="radio"]:checked::before{
    background-color: #321b83;
}

.custom-radio input[type="radio"]:checked::after{
    content: "";
    position: absolute;
    display: block;
    width: 11px;
    height: 6px;
    margin-top: -4px;
    top: 50%;
    left: 4px;
    transform: rotate(-45deg);
    border-bottom: 2px solid;
    border-left: 2px solid;
    border-color: #fff;
}

</style>