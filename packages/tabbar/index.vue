<template>
  <div class="van-tabbar van-hairline--top-bottom" :class="{ 'van-tabbar--fixed': fixed }">
    <slot></slot>
  </div>
</template>

<script>
import { create } from '../utils';

export default create({
  name: 'van-tabbar',

  data() {
    return {
      items: []
    };
  },

  props: {
    value: Number,
    fixed: {
      type: Boolean,
      default: true
    }
  },

  watch: {
    items() {
      this.setActiveItem();
    },
    value() {
      this.setActiveItem();
    }
  },

  methods: {
    setActiveItem() {
      this.items.forEach((item, index) => {
        item.active = index === this.value;
      });
    },
    onChange(active) {
      this.$emit('input', active);
      this.$emit('change', active);
    }
  }
});
</script>
