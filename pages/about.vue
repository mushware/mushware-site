<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title="Mushware"
      subtitle="Projects in four spatial dimensions"
      image="/uploads/about-hero.jpg"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="content">
          <h3>Mushware</h3>
          <p>
            Mushware was a real company until 2011. This site is an archive
            dedicated to its software project Adanaxis.
          </p>
        </div>
      </template>

      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: `About | ${this.$siteConfig.siteName}`
    }
  },
  components: {}
}
</script>
