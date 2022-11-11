<template>
  <button class="f-button" :class="{[`icon-${iconPosition}`]:true}">
    <f-icon class="icon" v-if="icon" :name="icon"/>
    <f-icon class="loading" name="loading"/>
    <div class="content">
      <slot/>
    </div>
  </button>
</template>
<script>
export default {

  props: {
    icon: {},
    iconPosition: {
      type: String,
      default: 'left',
      validator(value) {
        return value === 'right' && value === 'left';
      }
    }
  }
}
</script>
<style lang="scss">
@keyframes spin {
  0% {transform: rotate(0);}
  100% {transform: rotate(360deg)}
}

.f-button {
  font-size: var(--font-size);
  height: var(--button-height);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background: var(--button-bg);
  display: inline-flex;
  justify-content: center;
  align-items: center;
  vertical-align: middle;
  > .icon {order: 1;margin-right: .1em;}
  > .content {order: 2;}
  &.icon-right {
    > .icon {
      order: 2;
      margin-right: 0;
      margin-left: .1em;
    }

    > .content {
      order: 1;
    }
  }

  &:hover {
    border-color: var(--border-color-hover);
  }

  &:active {
    background-color: var(--button-active-bg);
  }

  &:focus {
    outline: none;
  }

  .loading {
    animation: spin 2s infinite linear;
  }
}
</style>