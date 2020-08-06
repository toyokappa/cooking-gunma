<template lang="pug">
.about
  .container
    .row
      .col-lg-6.mb-sx-3
        img(v-lazy="food")
      .col-lg-6
        .description
          | お料理やお菓子作りをキッカケにして参加者同士で友好を深められたらという想いで、前橋市を中心に「群馬お料理クラブ」を発足しました。
          br
          br
          | 老若男女、初心者・上級者問わず様々な方々にご参加いただいています。親子での参加ももちろん大歓迎。小さいお子様連れの場合、ベビーカー持参での参加も可能です。
          br
          br
          | お料理クラブとは別に精神福祉ボランティア活動も行っており、障害をお持ちの方でもお気軽に参加いただけます。
          br
          br
          | 群馬県は特産物が豊かなので、できる限り地域のお野菜を使うことで地産地消・地域活性化を兼ねています。
          br
          br
          | 共同作業で楽しくお料理をすることで、心身ともに笑顔で健康で過ごせる環境づくりを意識していますので、ご興味のある方はお気軽にご参加ください。
</template>

<script>
import cooking from "@/assets/images/cooking_sample.jpg";
import food from "@/assets/images/food.jpeg";

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