<template>
  <div>
    <div
      @click="opened = !opened"
      :style="{ 'margin-left': `${depth * 30}px` }"
      class="file"
    >
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
  data() {
    return {
      opened: false,
    };
  },
};
</script>

<style scoped lang="scss">
.file {
  display: flex;
  position: relative;
  color: rgb(46, 46, 46);
  width: 300px;
  line-height: 150%;
  margin-bottom: 8px;
  cursor: pointer;
  transition: all 0.1s ease-in-out;
  &:hover {
    background-color: rgba(17, 118, 233, 0.336);
    border-left: 3px solid rgba(17, 118, 233, 0.336);
  }
  span {
    display: block;
  }
}
</style>
