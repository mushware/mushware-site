<template>
  <section :class="`hero is-medium hero-theme-${computedTheme}`">
    <div class="wrap-banner">
      <div class="hero-body">
        <img
          class="hero-bg-img"
          :src="responsiveImage.src"
          :lazy="false"
          :srcset="responsiveImage.srcSet"
        />

        <div class="container">
          <h1 class="title animated fadeInUp">
            {{ title }}
          </h1>
          <h2 class="subtitle animated fadeInUp slower">
            {{ subtitle }}
          </h2>
          <br />
          <div
            v-if="$slots.default"
            class="under-subtitle animated fadeInDown slower"
          >
            <slot />
          </div>
        </div>
      </div>
      <div class="mush-particles">
        <client-only>
          <MushParticles
            color="#DCBA8F"
            :particles-number="100"
            shape-type="star"
            :particle-size="3"
            movement-direction="top"
            lines-color="#dedede"
            :line-linked="false"
            :move-speed="0.75"
          />
        </client-only>
      </div>
    </div>
  </section>
</template>

<script>
import MushParticles from '~/components/MushParticles.vue'

export default {
  name: 'SiteHero',
  components: {
    MushParticles
  },
  props: {
    title: { type: String, default: '' },
    subtitle: { type: String, default: '' },
    image: { type: String, default: '' },
    color: { type: String, default: '#469af0' },
    theme: { type: String, default: '' }
  },
  computed: {
    responsiveImage() {
      if (this.image.indexOf('/uploads') === 0) {
        return require(`~/assets${this.image}`)
      }
      return { src: this.image, srcSet: '' }
    },
    computedTheme() {
      if (this.theme === '' && this.$siteConfig.hero.theme) {
        return this.$siteConfig.hero.theme
      }
      return this.theme || 'mist'
    }
  }
}
</script>

<style lang="scss" scoped>
.hero {
  margin-top: 52px;
  background-size: cover !important;
  background-position: center;
  text-align: center;
  overflow: hidden;
  position: relative;
}

.title {
  font-weight: 300;
  @media (min-width: 768px) {
    font-size: 3.2rem;
  }
}
.subtitle,
.under-subtitle {
  padding: 0;
  margin: 0;
}
.subtitle {
  font-size: 1rem;
  margin-bottom: 0 !important;
}
.under-subtitle {
  display: inline-block;
  font-size: 0.8rem;
  border-top: 2px solid $primary;
  padding-top: 5px;
}
.opti-image {
  opacity: 0;
}
.opti-image-loaded {
  opacity: 0.12;
  animation: blurIn 4.5s ease;
}
</style>
<style lang="scss">
.hero {
  .hero-bg-img {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    object-fit: cover;
    width: 100%;
    height: 100%;
  }
  .opti-image {
    opacity: 0;
  }
  .opti-image-loaded {
    opacity: 1;
  }
}
.hero-theme-mist {
  .hero-bg-img {
    filter: grayscale(1);
  }
  .opti-image-loaded {
    opacity: 0.12;
    animation: blurInGrayscale 4.5s ease;
  }
}
.hero-theme-dark,
.hero-theme-light {
  &.hero:after {
    content: '';
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.65);
    position: absolute;
  }
  .hero-body {
    position: relative;
    z-index: 2;
  }
}
.hero-theme-dark {
  .title,
  .subtitle,
  .under-subtitle,
  .under-subtitle strong {
    color: white;
  }
}
.hero-theme-light.hero {
  &:after {
    background: rgba(255, 255, 255, 0.6);
  }
  .title,
  .subtitle,
  .under-subtitle,
  .under-subtitle strong {
    text-shadow: 1px 1px 2px white;
  }
}

.mush-particles {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.wrap-banner {
  position: relative;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  height: 100%;
  justify-content: center;
}
</style>
