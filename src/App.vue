<template>
  <div class="file-template">
    <div class="file-template__folder-section folder-section">
      <div class="folder-section__logo">
        <span class="explorer-logo"
          ><img src="./img/icons/explorer.svg" alt=""
        /></span>
        File Explorer
      </div>
      <div class="tools-panel__buttons">
        <div class="btn btn__left">&larr;</div>
        <div class="btn btn__right">&rarr;</div>
        <div class="btn btn__search">
          <img src="./img/icons/search1.svg" alt="search" />
        </div>
        <div class="btn btn__document">
          <img src="./img/icons/document.svg" alt="document" />
        </div>
        <div class="btn btn__share">
          <img src="./img/icons/share.svg" alt="share" />
        </div>
        <div class="btn btn__watch">
          <img src="./img/icons/binoculars.svg" alt="watch" />
        </div>
      </div>
      <div class="folder-section__content">
        <FolderView name="Files" :folders="folders" :files="files" />
      </div>
    </div>
    <div class="file-template__working-section working-section">
      <div class="working-section__tools-panel tools-panel">
        <div class="tools-panel__buttons">
          <div class="btn btn__left">&larr;</div>
          <div class="btn btn__right">&rarr;</div>
          <div class="btn btn__search">
            <img src="./img/icons/search.svg" alt="search" />
          </div>
          <div class="btn btn__document">
            <img src="./img/icons/document.svg" alt="document" />
          </div>
          <div class="btn btn__share">
            <img src="./img/icons/share.svg" alt="share" />
          </div>
          <div class="btn btn__watch">
            <img src="./img/icons/binoculars.svg" alt="watch" />
          </div>
        </div>
        <div class="tools-panel__app-buttons">
          <div class="btn btn__hide-window">&minus;</div>
          <div class="btn btn__resize">&harr;</div>
          <div class="btn btn__close">&times;</div>
        </div>
      </div>
      <div class="working-section__file-view">
        <span>File Preview here</span>
      </div>
    </div>
  </div>
</template>

<script>
import FolderView from "./components/FolderView.vue";
import FileView from "./components/FileView.vue";
import data from "./data/list";

export default {
  name: "App",
  components: {
    FolderView,
    FileView,
  },
  data: () => data,
};
</script>

<style lang="scss">
// BRAKEPOINTS
$md1: 999.98px;
$md2: 895.98px;
$md3: 479.98px;
$md4: 319.98px;
body {
  margin: 0;
  overflow-x: hidden;
}
#app {
  width: 100%;
  font-family: "Lato", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: -webkit-linear-gradient(to right, #50f2c4, #26d0e3, #757aff);
  background: linear-gradient(to right, #50f2c4, #26d0e3, #757aff);
  padding: 10px 0 10px 0;
  height: 100vh;
  @media (max-width: $md1) {
    padding: 0;
  }
  .file-template {
    display: flex;
    margin: 0 auto;
    max-width: 90%;
    height: 100%;
    border-radius: 5px;
    backdrop-filter: blur(10px);
    @media (max-width: $md1) {
      max-width: 100%;
      height: 100vh;
    }
  }
  // FOLDER SECTION
  .file-template__folder-section {
    width: 400px;
    height: 100%;
    background-color: rgba(235, 235, 235, 0.63);
    overflow: hidden;
    border-radius: 5px 0px 0px 5px;
    .tools-panel__buttons {
      display: none;
      @media (max-width: $md2) {
        display: flex;
        max-width: 250px;
      }
    }
    @media (max-width: $md1) {
      width: 40%;
    }
    @media (max-width: $md2) {
      width: 100%;
      border-radius: 0;
    }
  }
  .folder-section__content {
    height: 80%;
    overflow-y: auto;
    overflow-x: hidden;
  }
  .folder-section__logo {
    display: flex;
    margin-left: 10px;
    margin-bottom: 20px;
    max-width: 200px;
    align-items: center;
    font-size: 25px;
    font-weight: bold;
    border-bottom: 2px solid black;
    @media (max-height: $md3) {
      margin-bottom: 0;
    }
  }
  // .explorer-logo {
  // }
  // WORKING SECTION
  .file-template__working-section {
    width: 100%;
    border-radius: 0px 5px 5px 0px;
    overflow: hidden;
    background-color: rgba(202, 202, 202, 0.548);
    // rgba(202, 202, 202, 0.425);
    @media (max-width: $md1) {
      width: 60%;
    }
    @media (max-width: $md2) {
      display: none;
    }
  }
  .working-section__file-view {
    padding-top: 15%;
    display: flex;
    flex-direction: column;
    align-items: center;
    span {
      font-size: 40px;
      text-transform: uppercase;
    }
  }
  // TOOLS PANEL
  .working-section__tools-panel {
    width: 100%;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 10px;
  }
  .tools-panel__buttons {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 400px;
    transition: all 0.3s ease-in-out;
    padding-left: 10px;
  }
  // BUTTONS
  .btn {
    cursor: pointer;
    transition: all 0.3s linear;
    font-size: 40px;
    &:hover {
      transform: scale(1.05);
    }
  }
  .btn__left,
  .btn__right {
    margin-bottom: 10px;
    &:hover {
      transform: scale(1);
    }
    @media (max-width: $md2) {
      display: none;
    }
  }
  .tools-panel__app-buttons {
    display: flex;
    justify-content: space-between;
    width: 150px;
    margin-right: 40px;
    @media (max-width: $md1) {
      width: 70px;
    }
  }
  .btn__resize {
    font-size: 30px;
    transform: rotate(130deg);
    &:hover {
      transform: rotate(130deg) scale(1.05);
    }
    @media (max-width: $md1) {
      display: none;
    }
  }
  .tools-panel__search {
    font-size: 20px;
    margin-left: 10px;
    cursor: pointer;
  }
}
</style>
