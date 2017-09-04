<template>
  <input
    class="md-input"
    :type="type"
    :name="name"
    :value="value"
    :disabled="disabled"
    :required="required"
    :placeholder="placeholder"
    :maxlength="maxlength"
    :readonly="readonly"
    @focus="onFocus"
    @blur="onBlur"
    @input="onInputChange"
    @keydown.up="onInputChange"
    @keydown.down="onInputChange">
</template>

<script>
  import common from './common';
  import getClosestVueParent from '../../core/utils/getClosestVueParent';

  export default {
    name: 'md-input',
    props: {
      type: {
        type: String,
        default: 'text'
      },
      pattern: {
        type: String,
        default: 'XXX-XXX-XXXX'
      }
    },
    mixins: [common],
    mounted() {
      this.$nextTick(() => {
        this.parentContainer = getClosestVueParent(this.$parent, 'md-input-container');

        if (!this.parentContainer) {
          this.$destroy();

          throw new Error('You should wrap the md-input in a md-input-container');
        }

        this.parentContainer.inputInstance = this;
        this.setParentDisabled();
        this.setParentRequired();
        this.setParentPlaceholder();
        this.handleMaxLength();
        this.updateValues();
        if (this.type === 'tel') {
          this.formatPhone();
        }
      });
    },
    methods: {
      onInputChange(input) {
        if (this.type === 'tel') {
          this.formatPhone();
        }
        this.onInput(input);
      },
      formatPhone() {
        const pattern = this.pattern.trim();
        const value = this.$el.value.trim();
        let i = 0;

        const scrubbedValue = (value || '')
          .replace(/[^0-9]/g, '')
          .replace(/^[01]*/, '');

        const formattedValue = pattern
          .replace(/X/g, function replaceX() {
            return scrubbedValue[i++] || '';
          })
          .replace(/-*$/, '');

        if (formattedValue === value) {
          return;
        }

        const input = this.input;

        try {
          const caret = input.selectionStart +
            formattedValue.length -
            value.length;

          this.$el.value = formattedValue;

          input.selectionStart = caret;
          input.selectionEnd = caret;
        } catch (err) {
          this.$el.value = formattedValue;
        }
      }
    }
  };
</script>
