<template>
  <transition name="fade">
    <div v-if="show">
      Fade
    </div>
  </transition>
</template>

<style>
.fade-enter-active, .fade-leave-active {
  will-change: opacity;
  transition: opacity 225ms cubic-bezier(0.4, 0, 0.2, 1) 0ms;
}
.fade-enter, .fade-leave-to {
  opacity: 0
}
</style>