<script setup>
const { data: page } = await useAsyncData("index", () =>
  queryContent("/").findOne()
);
if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: "Page not found",
    fatal: true,
  });
}
definePageMeta({
  layout: "default",
});
</script>

<template>
  <Container>
    {{page.videos}}
    <video autoplay muted loop :src="page.videos.video1" type="video/mp4"></video>
    <video autoplay muted loop :src="page.videos.video2" type="video/mp4"></video>
    <video autoplay muted loop :src="page.videos.video3" type="video/mp4"></video>
    <Hero
      :title="page.hero.title"
      :description="page.hero.description"
      :image="page.hero.image"
      :imageAlt="page.hero.imageAlt"
      :buttons="page.hero.buttons"
    ></Hero>
    <Logos :title="page.logos.title" :icons="page.logos.icons"></Logos>
    <Features
      :title="page.features.title"
      :description="page.features.description"
      :items="page.features.items"
    > test</Features>
    <Testimonials
      :title="page.testimonials.title"
      :description="page.testimonials.description"
      :items="page.testimonials.items"
    ></Testimonials>
    <Cta
      :title="page.cta.title"
      :description="page.cta.description"
      :buttons="page.cta.buttons"
    ></Cta>
  </Container>
</template>
