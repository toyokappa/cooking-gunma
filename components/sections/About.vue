<template lang="pug">
.about
  .container
    .row.about-section
      .col-lg-6.order-lg-2.mb-sx-3
        img(v-lazy="cooking")
      .col-lg-6.order-lg-1
        .description
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
    .row
      .col-lg-6.mb-sx-3
        img(v-lazy="food")
      .col-lg-6
        .description
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
          br
          br
          | あああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああああ
</template>

<script>
import cooking from "@/assets/images/cooking_sample.jpg";
import food from "@/assets/images/food_sample.jpg";

export default {
  data() {
    return {
      cooking,
      food,
    };
  },
};
</script>

<style lang="sass" scoped>
.about
  .about-section
    margin-bottom: 150px
  img
    width: 100%
    @include media-breakpoint-down(md)
      margin-bottom: 15px
  .description
    color: $primary-grey
    font-size: 14px
    line-height: 1.7
</style>