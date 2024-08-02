<template>
  <footer>
    <div class="copyright">
      <n-text class="description" v-html="packageJson.description" />
      <span class="author" @click="jumpLink(authorUrl)">
        {{ authorText }}
      </span>
      <span> &nbsp;| API from</span>
      <span class="api-provider" @click="jumpLink(authorUrl)">
      aligu99
      </span>
      <span> &nbsp;| Designed by</span>
      <span class="designer" @click="jumpLink(designUrl)">
      imsyy
      </span>
    </div>
  </footer>
</template>

<script setup>
import packageJson from "@/../package.json";

const authorUrl = packageJson.github; // 使用作者的 GitHub 链接
const authorText = packageJson.author;
const designUrl = packageJson.GitHub;

// 链接跳转
const jumpLink = (url) => {
  window.open(url);
};
</script>

<style lang="scss" scoped>
footer {
  height: 100px;
  padding: 0 5vw;
  max-width: 1800px;
  margin: 20px auto 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  .copyright {
    display: flex;
    align-items: center;
    margin-bottom: 4px;
    .description {
      &::after {
        content: "@ Copyright By";
        margin: 0 6px;
      }
    }
  }

  .author, .api-provider, .designer {
    cursor: pointer;
    transition: all 0.3s;
    color: grey; /* 更浅的颜色 */
    &:hover {
      color: var(--n-code-text-color); /* 更深的颜色 */
    }
  }

  .api-provider, .designer {
    margin-left: 2px; /* 减小间距 */
  }

  span:not(.author):not(.api-provider):not(.designer) {
    margin: 0 1px; /* 减小间距 */
  }

  .clickable {
    cursor: pointer;
  }
}
</style>
