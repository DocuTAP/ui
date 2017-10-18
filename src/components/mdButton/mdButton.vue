<template>
  <a class="md-button" :class="[themeClass]" :href="href" :faux-link="fauxLink" :disabled="disabled" :target="target" :rel="newRel" @click="$emit('click', $event)" v-if="href">
    <md-ink-ripple :md-disabled="disabled" v-if="!fauxLink"></md-ink-ripple>
    <slot></slot>
  </a>

  <button class="md-button" :class="[themeClass]" :type="type" :faux-link="fauxLink" :disabled="disabled" @click="$emit('click', $event)" v-else>
    <md-ink-ripple :md-disabled="disabled" v-if="!fauxLink"></md-ink-ripple>
    <slot></slot>
  </button>
</template>

<style lang="scss" src="./mdButton.scss"></style>

<script>
  import theme from '../../core/components/mdTheme/mixin';

  export default {
    name: 'md-button',
    props: {
      href: String,
      target: String,
      rel: String,
      type: {
        type: String,
        default: 'button'
      },
      fauxLink: {
        type: Boolean,
        default: false
      },
      disabled: Boolean
    },
    mixins: [theme],
    computed: {
      newRel() {
        if (this.target === '_blank') {
          return this.rel || 'noopener';
        }

        return this.rel;
      }
    }
  };
</script>
