<template lang="pug">
  .lesson
    .container
      .row
        .offset-lg-1.col-lg-10
          .recipe-image(v-lazy:backgroundImage="recipe")
          .recipe-title 米粉を作ったバタークッキー
          .recipe-description ああああああああああああああああああああああああああああああああああああああああああ
          .lesson-at
            .label
              i.fa.fa-calendar-alt.mr-2
              span 開催日時
            .item
              span.value 2020
              span.unit 年
              span.value 7
              span.unit 月
              span.value 18
              span.unit.mr-2 日(土)
              span.value 11:00
              span.unit 開始
          .lesson-fee
            .label
              i.fa.fa-yen-sign.mr-2
              span 受講料
            .item
              span.value 5,000
              span.unit 円(税込)
            .excuse お支払い方法についてはxxxxx
</template> 

<script>
import recipe from "@/assets/images/recipe_sample.jpg";

export default {
  data() {
    return {
      recipe
    };
  }
};
</script>

<style lang="sass" scoped>
.lesson
  .recipe-image
    width: 100%
    padding-bottom: 60%
    background-size: cover
    background-position: center center
    margin-bottom: 5px
  .recipe-title
    font-family: $ja-accent-family
    margin-bottom: 5px
  .recipe-description
    margin-bottom: 30px
  @include media-breakpoint-up(sm)
    .recipe-title
      font-size: 28px
    .recipe-description
      font-size: 16px
  @include media-breakpoint-down(xs)
    .recipe-title
      font-size: 20px
    .recipe-description
      font-size: 14px
  .lesson-at, .lesson-fee
    margin-bottom: 30px
    .label
      color: $primary-grey
      font-size: 20px
      font-weight: bold
      margin-bottom: 8px
    .item
      font-weight: bold
      .value
        font-size: 22px
      .unit
        font-size: 14px
    .excuse
      color: $primary-grey
      font-size: 14px
</style>