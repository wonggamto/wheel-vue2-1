<template>
  <button class="g-button" :class="{[`icon-${iconPosition}`]:true}">
    <svg v-if="icon" class="icon" aria-hidden="true">
      <use :xlink:href=`#g-${icon}`></use>
    </svg>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>
<script>
export default {
  // props: ['icon', 'iconPosition']
  props:{
    icon:{},
    iconPosition:{
      type:String,
      default:'left',
      // 检测用户传进来的值是否合法
      validator(value) {
        return !(value !== 'left' && value !== 'right');
      }
    }
  }
}
</script>
<style lang="scss">
.g-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  // 防止内联元素无法上下对齐，这是因为inline引起的
  vertical-align: middle;
  font-size: var(--font-size);
  height: var(--button-height);
  padding: 0 .7em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background: var(--button-bg);

  &:hover {
    border-color: var(--border-color-hover);
  }

  &:active {
    background-color: var(--button-active-bg);
  }

  &:focus {
    outline: none;
  }

  .content {
    order: 2;
  }

  .icon {
    order: 1;
    margin-left: 0;
    margin-right: .6em;
  }

  &.icon-right {
    .content {
      order: 1;
    }

    .icon {
      order: 2;
      margin-right: 0;
      margin-left: .6em;
    }
  }
}

</style>
