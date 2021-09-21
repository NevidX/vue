<template>
  <div>
    <div :style="{ 'margin-left': `${depth * 30}px` }" class="file">
      <span>
        <img src="../img/icons/file.svg" alt="file" />
      </span>
      {{ name }}
    </div>
  </div>
</template>

<script>
export default {
  name: "FileView",
  props: {
    name: String,
    files: Array,
    depth: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style scoped lang="scss">
.file {
  position: relative;
  color: green;
  line-height: 150%;
  margin-bottom: 8px;
  cursor: pointer;
  span {
    display: block;
    position: absolute;
    left: -25px;
  }
}
</style>
