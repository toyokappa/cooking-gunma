<template lang="pug">
.welcome
  #pageTop.page-top(v-lazy:backgroundImage="topImage")
    .title-area
      .title-lg
        img(v-lazy="logoIcon")
        span Cooking Gunma
      .subtitle 誰でも気軽に楽しくお料理を
    .user-icon(v-lazy:backgroundImage="profile.fields.photo.fields.file.url")
  #profile.profile
    .name {{ profile.fields.name }}
    .name-alpha {{ profile.fields.furigana }}
    .job-title {{ profile.fields.title }}
    .introduction(v-html="parseDescription(profile.fields.introduction)")
</template>

<script>
import descriptionParserMixin from "@/components/mixins/descriptionParserMixin";
import topImage from "~/assets/images/top_image.jpg";
import logoIcon from "~/assets/images/logo_icon_white.svg";
import userIcon from "~/assets/images/user_icon.jpg";

export default {
  mixins: [descriptionParserMixin],
  data() {
    return {
      topImage,
      logoIcon,
      userIcon,
    };
  },
  props: {
    profile: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="sass" scoped>
.page-top
  position: relative
  width: 100%
  height: 100vh
  background-size: cover
  background-position: center center
  margin-bottom: 60px
  &:after
    content: ''
    width: 100%
    height: 100vh
    background-color: rgba(0, 0, 0, 0.3)
    position: absolute
    top: 0
    left: 0
  .title-area
    position: absolute
    top: 50%
    left: 50%
    transform: translateX(-50%) translateY(-50%)
    color: white
    font-family: $en-accent-family
    text-align: center
    width: 100%
    margin: auto
    z-index: 100
    @include media-breakpoint-up(sm)
      .title-lg
        font-size: 60px
        img
          height: 80px
          margin-right: 12px
          position: relative
          bottom: 15px
      .title-sm
        font-size: 54px
        font-weight: bold
        letter-spacing: 5px
      .subtitle
        font-size: 24px
        letter-spacing: 3px
    @include media-breakpoint-down(xs)
      .title-lg
        font-size: 36px
        img
          height: 50px
          margin-right: 8px
          position: relative
          bottom: 10px
      .title-sm
        font-size: 30px
        font-weight: bold
        letter-spacing: 5px
      .subtitle
        font-size: 16px
        letter-spacing: 3px
  .user-icon
    position: absolute
    bottom: -75px
    left: 50%
    transform: translateX(-50%)
    width: 150px
    height: 150px
    border-radius: 50%
    border: 3px solid white
    background-size: cover
    background-position: center center
    z-index: 1
.profile
  font-family: $en-accent-family
  text-align: center
  max-width: 360px
  margin: 0 auto
  padding-top: 80px
  .name
    font-family: $ja-accent-family
    font-size: 40px
    letter-spacing: 5px
  .name-alpha
    font-size: 20px
    letter-spacing: 4px
    margin-bottom: 20px
  .job-title
    color: $secondary-grey
    letter-spacing: 3px
    margin-bottom: 40px
</style>