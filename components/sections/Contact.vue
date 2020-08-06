<template lang="pug">
.contact
  .contact-wrapper.container
    .row
      .offset-lg-3.offset-md-2.col-lg-6.col-md-8
        form.contact-form(@submit="sendMail")
          .form-group
            label.sr-only(for="inputCategory") Category
            select#inputCategory.form-control(
              name="inputCategory",
              v-model="contactForm.category",
              required
            )
              option(value="", disabled) 問い合わせ種別
              option(value="レッスン参加のお申し込み") レッスン参加のお申し込み
              option(value="お料理教室についてのお問い合わせ") お料理教室についてのお問い合わせ
              option(value="その他") その他
          .form-group
            label.sr-only(for="inputName") お名前
            input#inputName.form-control(
              type="text",
              placeholder="お名前",
              name="inputName",
              v-model="contactForm.name",
              required
            )
          .form-group
            label.sr-only(for="inputEmail") メールアドレス
            input#inputEmail.form-control(
              type="email",
              placeholder="メールアドレス",
              name="inputEmail",
              v-model="contactForm.email",
              required
            )
          .form-group
            label.sr-only(for="inputMessage") 本文
            textarea#inputMessage.form-control(
              placeholder="本文",
              name="inputMessage",
              rows="5",
              v-model="contactForm.message"
            )
          .button-area
            button#submitButton.btn.btn-default.btn-submit(type="submit")
              i.fas.fa-check.mr-2
              | SUBMIT
    // ul.social-links
    //   li.item
    //     a.link(href="https://twitter.com/xxx", target="new")
    //       i.fab.fa-twitter
    //   li.item
    //     a.link(href="https://www.facebook.com/xxx", target="new")
    //       i.fab.fa-facebook-square
    //   li.item
    //     a.link(href="https://instagram.com/xxx", target="new")
    //       i.fab.fa-instagram
    //   li.item
    //     a.link(href="https://www.youtube.com/channel/xxx", target="new")
    //       i.fab.fa-youtube
</template>

<script>
export default {
  data() {
    return {
      contactForm: {
        category: "",
        name: "",
        email: "",
        message: "",
      },
    };
  },
  mounted() {
    this.$parent.$on("submitLesson", this.selectLesson);
  },
  methods: {
    async sendMail(e) {
      e.preventDefault();
      this.$nuxt.$loading.start();
      const mailer = this.$firebaseFunctions.httpsCallable("sendMail");
      try {
        await mailer(this.contactForm);
        this.$toast.success(
          "お問い合わせを受け付けました。ありがとうございました。",
          { duration: 5000 }
        );
        this.resetForm();
      } catch (err) {
        this.$toast.error(
          "お問い合わせに失敗しました。時間をおいて再度お試しください。",
          { duration: 5000 }
        );
        console.log(err);
        throw err;
      } finally {
        this.$nuxt.$loading.finish();
      }
    },
    resetForm() {
      this.contactForm = { category: "", name: "", email: "", message: "" };
    },
    selectLesson() {
      this.contactForm.category = "レッスン参加のお申し込み";
    },
  },
};
</script>

<style lang="sass" scoped>
.contact
  .form-group
    margin-bottom: 5px
  select, input, textarea
    height: auto
    background-color: white
    border-radius: 0
    border: none
    padding: 15px
    margin: 0
    box-shadow: none
    resize: none
    outline: none
    &:focus
      background-color: white
      box-shadow: none
      outline: none
  .btn-submit
    display: block
    background-color: #fa4f3e
    color: white
    font-family: $en-accent-family
    font-size: 15px
    letter-spacing: 3px
    border: none
    padding: 15px 25px
    margin-left: auto
  .social-links
    list-style: none
    text-align: center
    margin-top: 100px
    .item
      display: inline
      .link
        color: #F2BDD0
    @include media-breakpoint-up(sm)
      .item
        font-size: 36px
        margin: 0 15px
    @include media-breakpoint-up(xs)
      .item
        font-size: 30px
        margin: 0 10px
</style>