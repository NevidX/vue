
<template>
  <div class="wrapper">
    <div :style="{ 'margin-left': `${depth * 40}px` }" class="folder">
      <span><img src="../img/icons/folder.svg" alt="folder" /></span>{{ name }}
    </div>
    <template v-for="folder in folders">
      <!-- eslint-disable-next-line -->
      <FolderView
        :name="folder.name"
        :folders="folder.folders"
        :files="folder.files"
        :depth="depth + 1"
      />
    </template>
    <template v-for="file in files">
      <!-- eslint-disable-next-line -->
      <FileView :name="file.name" :file="file.files" :depth="depth + 1" />
    </template>
  </div>
</template>

<script>
import FileView from "./FileView";
export default {
  name: "FolderView",
  components: { FileView },
  props: {
    name: String,
    folders: Array,
    files: Array,
    depth: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrapper {
  .folder {
    font-weight: bold;
    position: relative;
    color: red;
    text-align: left;
    font-size: 20px;
    margin-bottom: 20px;
    cursor: pointer;
    span {
      display: block;
      position: absolute;
      top: -15px;
      left: -50px;
      transform: scale(0.5);
    }
  }
}
</style>
