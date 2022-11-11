<template>
    <svg class="f-icon">
      <use :xlink:href="`#i-${name}`"></use>
    </svg>
</template>

<script>
export default {
  props:['name']
}
</script>
<style>
.f-icon {
  height: 1em;
  width: 1em;

}
</style>