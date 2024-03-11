<template>
  <h5 class="ink-h project-heading">
    {{ heading }}
  </h5>
  <div v-for="project in projectList" :key="project.id">
    <a :href="project.html_url" class="project-item" target="_blank">
      <div class="project-image">
        <img :src="project.img_url" />
      </div>
      <div class="project-info">
        <div class="project-info--name text-theme-primary">
          {{ project.name }}
        </div>
        <div class="project-info--taglist">
          <span class="tag" v-for="tag in project.tagList" :key="tag">{{
            tag
          }}</span>
        </div>
        <div class="project-info--description">
          {{ project.description }}
        </div>
      </div>
    </a>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const heading = ref("recent projects");
const projectList = ref([
  {
    name: "2024-Algorithm",
    id: 738048262,
    description: "Too Hard！",
    html_url: "https://github.com/Gao-kai/2024-Algorithm",
    tagList: ["数组", "队列/栈", "二分法", "链表", "二叉树", "贪心算法"],
    img_url: "/public/assets/algo.png",
  },
  {
    name: "GKBlog",
    id: 770139735,
    description: "This is a good blog by astro framework!",
    html_url: "https://github.com/Gao-kai/GKBlog",
    tagList: [
      "Astro",
      "SSR服务端渲染",
      "Vue",
      "TypeScript",
      "Tailwind",
      "markdown",
    ],
    img_url: "/public/assets/blog.png",
  },
  {
    name: "react-fullstack-lowcode",
    id: 769421969,
    description: "Full Stack low Code platform based on React+Nuxt+Nest。",
    html_url: "https://github.com/Gao-kai/react-fullstack-lowcode",
    tagList: [
      "React18",
      "Nuxt.js",
      "TypeScript",
      "Nest",
      "Node.js",
      "pnpm+workspace",
    ],
    img_url: "/public/assets/lowcode.png",
  },
]);
const navToGithub = (url) => {
  window.open(url);
};
// fetch("https://api.github.com/users/Gao-kai/repos?per_page=100", {
//   method: "GET",
//   headers: {
//     Accept: "application/vnd.github.v3+json",
//     Authorization: "token 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",
//   },
// })
//   .then((response) => response.json())
//   .then((data) => {
//     console.log(data);
//     projectList.value = data
//       .filter((item) =>
//         ["GKBlog", "react-fullstack-lowcode", "2024-Algorithm"].includes(
//           item.name
//         )
//       )
//       .map((item) => {
//         return {
//           name: item.name,
//           id: item.id,
//           description: item.description,
//           html_url: item.html_url,
//         };
//       });
//   });
</script>

<style lang="scss">
.dark {
  .project-item {
    background-color: #32374b;
  }
}
</style>

<style lang="scss">
.project-heading {
  padding-left: 0;
}

.project-item {
  display: flex;
  background: #e7def2;
  justify-content: space-between;
  gap: 20px;
  margin-bottom: 20px;
  border-radius: 6px;
  overflow: hidden;
  cursor: pointer;
  box-sizing: border-box;
  padding: 12px;
  align-items: center;

  .project-image {
    width: 10rem;
    height: 10rem;

    > img {
      width: 100%;
      height: 100%;
    }
  }

  .project-info {
    width: 0;
    flex: 1;
    .project-info--name {
      font-size: 1.5rem;
      line-height: 1.75rem;
      font-weight: 600;
    }

    .project-info--taglist {
      display: flex;
      flex-wrap: wrap;
      column-gap: 10px;
      margin-top: 12px;
      .tag {
        background: #e879f9;
        padding: 6px;
        border-radius: 5px;
        font-size: 12px;
      }
    }

    .project-info--description {
      color: gray;
      margin-top: 10px;
    }
  }
}
@media (min-width: 640px) {
  .project-heading {
    padding-left: 1.5rem;
  }
}
</style>
