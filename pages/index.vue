<template lang="pug">
  #wrapper
    g-header
    section.section
      s-page-top
    section.section
      p-section-header#about(
        title="群馬お料理クラブ"
        subtitle="About Gunma Cooking Club"
        description="お料理教室への想い"
      )
      s-about
    section.section
      p-section-header#blog(
        title="最新情報"
        subtitle="Recent Blog Posts"
        description="最新の動向をコンテンツとしてお届け"
      )
      s-blog(:blogPosts="blogPosts")
      p-blog-link-button
    section.section
      p-section-header#lesson(
        title="次回の献立"
        subtitle="Next Cooking Recipe"
        description="美味しく楽しくともに学ぶ"
      )
      s-lesson
    section.section.section-grey
      p-section-header#contact(
        title="お問い合わせ"
        subtitle="Get In Touch"
        description="些細なことでも お気軽に ご相談ください"
        titleColor="#63AEE5"
        subtitleColor="black"
      )
      s-contact
    g-footer
</template>

<script>
import GHeader from "@/components/global/Header";
import GFooter from "@/components/global/Footer";
import PSectionHeader from "@/components/parts/SectionHeader";
import PBlogLinkButton from "@/components/parts/BlogLinkButton";
import SPageTop from "@/components/sections/PageTop";
import SAbout from "@/components/sections/About";
import SBlog from "@/components/sections/Blog";
import SLesson from "@/components/sections/Lesson";
import SContact from "@/components/sections/Contact";

export default {
  components: {
    GHeader,
    GFooter,
    PSectionHeader,
    PBlogLinkButton,
    SPageTop,
    SAbout,
    SBlog,
    SLesson,
    SContact
  },
  async asyncData({ app }) {
    const blogRes = await app.$ctfClient.getEntries({
      content_type: "blogPosts",
      order: "-sys.createdAt",
      limit: 3
    });
    const blogPosts = blogRes.items;

    return {
      blogPosts
    };
  },
  head() {
    const pageTitle = "群馬お料理クラブ Official Site";
    // const imageUrl = "https://learndeleon.com/twitter_image.jpg";
    const description =
      "群馬県にて定期開催をしている料理教室「群馬お料理クラブ」の公式サイトです。「誰でも気軽に楽しくお料理を」をコンセプトにお料理体験を提供しています。";
    return {
      title: pageTitle,
      meta: [
        { name: "description", content: description },
        { name: "twitter:card", content: "summary_large_image" },
        // { name: "twitter:image", content: imageUrl },
        { name: "twitter:title", content: pageTitle },
        { name: "twitter:description", content: description },
        { property: "og:title", content: pageTitle },
        { property: "og:type", content: "website" },
        // { property: "og:image", content: imageUrl },
        { property: "og:description", content: description }
      ]
    };
  }
};
</script>

<style lang="sass">
</style>
