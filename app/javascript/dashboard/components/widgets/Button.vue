<template>
  <button :type="type" class="button nice" :class="variant" @click="onClick">
    <i
      v-if="!isLoading && icon"
      class="icon"
      :class="buttonIconClass + ' ' + icon"
    />
    <spinner v-if="isLoading" />
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    isLoading: {
      type: Boolean,
      default: false,
    },
    icon: {
      type: String,
      default: '',
    },
    buttonIconClass: {
      type: String,
      default: '',
    },
    type: {
      type: String,
      default: 'button',
    },
    variant: {
      type: String,
      default: 'primary',
    },
  },
  methods: {
    onClick(e) {
      this.$emit('click', e);
    },
  },
};
</script>

<style scoped>
.icon {
  font-size: var(--font-size-large) !important;
}
</style>
