<template>
  <a :href="href" target="_blank" aria-label="Contact link" class="contact-link">
    <img :src="computedImgSrc" :alt="alt" class="icon" />
    {{ text }}
  </a>
</template>

<script>
export default {
  props: {
    href: String,
    imgSrc: String,
    alt: String,
    text: String,
  },
  data() {
    return {
      computedImgSrc: '',
    }
  },
  mounted() {
    this.formatImagePath()
  },
  methods: {
    formatImagePath() {
      if (this.imgSrc.startsWith('@/')) {
        this.computedImgSrc = this.imgSrc.replace('@/', '/src/')
      } else {
        this.computedImgSrc = this.imgSrc
      }
    },
  },
}
</script>

<style scoped>

.contact-link:focus {
  outline: none;
  box-shadow: none;
}

.contact-link:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.icon {
  width: 32px;
  height: 32px;
  margin-right: 10px;
  filter: invert(100%);
}
</style>
