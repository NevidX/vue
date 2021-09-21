
<template>
  <div class="wrapper">
    <div
      @click="opened = !opened"
      :style="{ 'margin-left': `${depth * 40}px` }"
      class="folder"
    >
      <span v-if="opened" class="folder-icon"
        ><img src="../img/icons/folder.svg" alt="folder"
      /></span>
      <span v-else class="closed-folder-icon">
        <img src="../img/icons/ClosedFolder.svg" alt="folder" />
      </span>
      {{ name }}
    </div>
    <template v-for="folder in folders">
      <!-- eslint-disable-next-line -->
      <FolderView
        v-if="opened"
        :name="folder.name"
        :folders="folder.folders"
        :files="folder.files"
        :depth="depth + 1"
      />
    </template>
    <template v-for="file in files">
      <!-- eslint-disable-next-line -->
      <FileView
        v-if="opened"
        :name="file.name"
        :file="file.files"
        :depth="depth + 1"
      />
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
  data() {
    return {
      opened: false,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.wrapper {
  width: 350px;
  &:first-child {
    border: 5px solid gray;
    border-radius: 30px;
    padding: 20px 0 0 60px;
  }
  .folder {
    font-weight: bold;
    position: relative;
    color: rgb(122, 122, 122);
    text-align: left;
    font-size: 20px;
    margin-bottom: 10px;
    cursor: pointer;
    transition: background 0.3s ease-in-out;
    &:hover {
      background-color: rgba(17, 118, 233, 0.336);
    }
    .folder-icon,
    .closed-folder-icon {
      display: block;
      position: absolute;
      top: -15px;
      left: -45px;
      transform: scale(0.4);
    }
  }
}
</style>
