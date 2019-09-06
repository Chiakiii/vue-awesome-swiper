<template>
  <div :class="slideClass">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'swiper-slide',
    data() {
      return {
        slideClass: 'swiper-slide'
      }
    },
    ready() {
      this.update()
    },
    mounted() {
      this.update()
      if (this.$parent && this.$parent.options && this.$parent.options.slideClass) {
        this.slideClass = this.$parent.options.slideClass
      }
    },
    updated() {
      if (this.$parent.options && this.$parent.options.isUpdate) {
        this.update()
      }
    },
    attached() {
      this.update()
    },
    methods: {
      update() {
        if (this.$parent && this.$parent.swiper) {
          this.$parent.update()
        }
      }
    }
  }
</script>
