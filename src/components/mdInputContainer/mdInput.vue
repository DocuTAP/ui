<template>
  <input
    class="md-input"
    :type="typeOutput"
    :name="name"
    :value="value"
    :disabled="disabled"
    :required="required"
    :placeholder="placeholder"
    :maxlength="maxlength"
    :readonly="readonly"
    :spellcheck="spellcheck"
    @focus="onFocus"
    @blur="onInputBlur"
    @input="onInputChange"
    @keydown.up="onInputChange"
    @keydown.down="onInputChange">
</template>

<script>
  const moment = require('moment');

  moment.suppressDeprecationWarnings = true;

  import common from './common';
  import getClosestVueParent from '../../core/utils/getClosestVueParent';

  export default {
    name: 'md-input',
    props: {
      type: {
        type: String,
        default: 'text'
      },
      spellcheck: {
        type: Boolean
      },
      phonePattern: {
        type: String,
        default: 'XXX-XXX-XXXX'
      },
      datePattern: {
        type: String,
        default: 'MM/DD/YYYY'
      }
    },
    data() {
      return {
        typeOutput: 'text'
      };
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
        this.typeOutput = this.type;
        if (this.type === 'tel') {
          this.$nextTick(() => this.formatPhone());
        }
        if (this.type === 'date') {
          this.typeOutput = 'text';
        }
      });
    },
    methods: {
      onInputChange(input) {
        if (this.type === 'tel') {
          this.formatPhone();
          this.$nextTick(() => this.onInput());
        }
        this.onInput(input);
      },
      onInputBlur(input) {
        if (this.type === 'date') {
          this.formatDate();
          this.$nextTick(() => this.onInput());
        }
        this.onBlur(input);
      },
      formatDate() {
        const pattern = this.datePattern.trim();
        const value = this.$el.value.trim();

        if (!value) {
          return;
        }

        let date = moment(value);

        if (!date.isValid()) {
          date = moment(value, 'MMDDYYYY');
        }

        if (!date.isValid()) {
          return;
        }

        const formattedValue = date.format(pattern);

        if (formattedValue === value) {
          return;
        }

        const input = this.$el;

        if (!input) {
          return;
        }

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
      },
      formatPhone() {
        const pattern = this.phonePattern.trim();
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
