<template>
  <div>
    <transition name="fade">
      <div v-if="isOpen" class="drawer-overlay" @click="closeDrawer"></div>
    </transition>
    <transition name="slide-up">
      <div v-if="isOpen" ref="drawer" class="drawer" :style="{ width }">
        <div class="drawer-header">
          <span class="drawer-header-drag-handle"></span>
        </div>
        <slot></slot>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Boolean,
      default: false,
    },
    width: {
      type: String,
      default: '375px',
    },
  },
  data() {
    return {
      isOpen: this.value,
      startY: 0,
      currentY: 0,
    }
  },
  watch: {
    value(newVal) {
      this.isOpen = newVal
    },
    isOpen(newVal) {
      this.$emit('input', newVal)
    },
  },
  methods: {
    startDrag(event) {
      this.startY = event.touches[0].clientY
    },
    dragging(event) {
      this.currentY = event.touches[0].clientY
      const translateY = this.currentY - this.startY

      if (translateY > 0 && this.$refs.drawer) {
        this.$refs.drawer.style.transform = `translateY(${translateY}px)`
      }
    },
    endDrag() {
      const translateY = this.currentY - this.startY
      if (translateY > 100) {
        this.closeDrawer()
      } else if (this.$refs.drawer) {
        this.$refs.drawer.style.transform = 'translateY(0px)'
      }
    },
    closeDrawer() {
      this.isOpen = false
    },
  },
}
</script>

<style lang="scss" scoped>
.drawer-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
}

.drawer {
  position: fixed;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: v-bind(width);
  background: #121119;
  border-radius: 12px 12px 0 0;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.2);
  z-index: 1000;
  transition: transform 0.3s ease;

  &-header {
    padding: 12px;
    text-align: center;

    &-drag-handle {
      width: 52px;
      height: 6px;
      background: #888;
      border-radius: 2px;
      display: block;
      margin: 0 auto;
    }
  }
}

.fade {
  &-enter-active,
  &-leave-active {
    transition: opacity 0.3s ease;
  }

  &-enter-from,
  &-leave-to {
    opacity: 0;
  }
}

.slide-up {
  &-enter-active,
  &-leave-active {
    transition: transform 0.3s ease;
  }

  &-enter-from,
  &-leave-to {
    transform: translate(-50%, 100%);
  }

  &-enter-to,
  &-leave-from {
    transform: translate(-50%, 0);
  }
}
</style>
