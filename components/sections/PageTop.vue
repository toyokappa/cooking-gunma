<template lang="pug">
  .welcome
    #pageTop.page-top(v-lazy:backgroundImage="topImage")
      .title-area
        .title-lg Gunma Cooking Club
        .subtitle 誰でも気軽に楽しくお料理を
      .user-icon(v-lazy:backgroundImage="userIcon")
    #profile.profile
      .name 松井 なおこ
      .name-alpha Matsui Naoko
      .job-title cooking club organizer, patissier, cooking specialist
</template>

<script>
import topImage from "~/assets/images/top_image.jpg";
import userIcon from "~/assets/images/user_icon.jpg";

export default {
  data() {
    return {
      topImage,
      userIcon
    };
  }
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
    background-color: rgba(0, 0, 0, 0.2)
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
        font-weight: bold
        letter-spacing: 5px
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
        font-weight: bold
        letter-spacing: 5px
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
  margin: 0 auto 180px
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
</style>