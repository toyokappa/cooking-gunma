<template lang="pug">
.section-header
  .section-title(:style="`color: ${titleColor};`") {{ title }}
  .section-subtitle(:style="`color: ${subtitleColor};`") {{ subtitle }}
  .section-description {{ description }}
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      require: true,
    },
    titleColor: {
      type: String,
      default: "black",
    },
    subtitleColor: {
      type: String,
      default: "black",
    },
  },
};
</script>

<style lang="sass" scoped>
.section-header
  text-align: center
  padding-top: 80px
  padding-bottom: 100px
  .section-title
    font-family: $ja-accent-family
    letter-spacing: 5px
    margin-bottom: 0
  .section-subtitle
    font-family: $en-accent-family
    font-size: 20px
    font-weight: normal
    letter-spacing: 4px
    margin-bottom: 30px
  .section-description
    color: $secondary-grey
    font-size: 16px
    font-weight: normal
    letter-spacing: 3px
  @include media-breakpoint-up(sm)
    .section-title
      font-size: 40px
    .section-description
      font-size: 16px
  @include media-breakpoint-down(xs)
    .section-title
      font-size: 36px
    .section-description
      font-size: 14px
      padding: 0 10px
</style>