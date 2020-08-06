<template lang="pug">
.lesson
  .container(v-if="lesson")
    .row
      .offset-lg-1.col-lg-10
        .recipe-image(
          v-lazy:backgroundImage="lesson.fields.image.fields.file.url"
        )
        .recipe-title {{ lesson.fields.title }}
        .recipe-description(
          v-html="parseDescription(lesson.fields.description)"
        )
        .lesson-at
          .label
            i.fa.fa-calendar-alt.mr-2
            span 開催日時
          .item
            span.value {{ lessonAtArray[0] }}
            span.unit 年
            span.value {{ lessonAtArray[1] }}
            span.unit 月
            span.value {{ lessonAtArray[2] }}
            span.unit.mr-2 日({{ lessonAtArray[3] }})
            span.value {{ lessonAtArray[4] }}
            span.unit 開始
        .lesson-location
          .label
            i.fa.fa-map-marker-alt.mr-2
            span 開催場所
          .item
            .value {{ lesson.fields.location }}
        .lesson-fee
          .label
            i.fa.fa-yen-sign.mr-2
            span 受講料
          .item
            span.value {{ lesson.fields.fee.toLocaleString() }}
            span.unit 円(税込)
          .excuse お支払い方法については、当日の手渡しでお願いしております。
        .lesson-submit
          .submit-button(@click="submitLesson") レッスンに参加する
  .container(v-else)
    .preparing 準備中です。しばしお待ち下さい。
</template> 

<script>
import datetimeParserMixin from "@/components/mixins/datetimeParserMixin";
import descriptionParserMixin from "@/components/mixins/descriptionParserMixin";
import recipe from "@/assets/images/recipe_sample.jpg";

export default {
  mixins: [datetimeParserMixin, descriptionParserMixin],
  data() {
    return {
      recipe,
      lessonAtArray: [],
    };
  },
  props: {
    lesson: {
      type: Object,
    },
  },
  mounted() {
    this.lessonAtArray = this.parseDatetimeArray(this.lesson.fields.lessonAt);
  },
  methods: {
    submitLesson() {
      console.log(this);
      this.$parent.$emit("submitLesson");
      this.$scrollTo("#contact");
    },
  },
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
  .lesson-at, .lesson-location, .lesson-fee
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
  .lesson-submit
    text-align: center
    margin-top: 50px
    .submit-button
      display: inline-block
      color: white
      font-size: 24px
      background-color: $accent-color
      padding: 12px 24px
      border: 3px solid $accent-color
      border-radius: 5px
      cursor: pointer
      transition: 0.3s
      &:hover
        color: $accent-color
        background-color: white
  .preparing
    text-align: center
    font-size: 20px
    font-weight: bold
</style>