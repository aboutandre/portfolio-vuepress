<template>
  <div class="project-list">

    <router-link
      :to="post.path"
      tag="div"
      v-for="post in posts"
      :key="post.title"
      class="post"
      :style="{ backgroundImage: `url(${post.frontmatter.thumbnail})` }"
    >

      <div class="info">
        <h2>{{ post.frontmatter.title }}</h2>
        <span v-if="post.frontmatter.description">{{ post.frontmatter.description }}</span>
      </div>

    </router-link>

  </div>
</template>

<script>
  export default {
    computed: {
      posts() {
        return this.$site.pages
          .filter(x => x.path.startsWith('/works/') && !x.frontmatter.works_index)
          .sort((a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date))
      }
    }
  }
</script>

<style scoped>

.project-list {
  display: flex;
  flex-wrap: wrap;
}

  .post {
    position: relative;
    width: 100%;
    height: 35vh;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    margin-bottom: 5vw;
    cursor: pointer;
  }

  @media screen and (min-width: 620px) {
    .project-list {
      margin: -1.2rem;
    }
    .post {
      margin: 1.2rem;
      width: calc(50% - 2.4rem);
    }
  }

  .info {
    position: absolute;
    left: 0;
    top: 2rem;
    padding: 0.5rem 1rem;
    background: rgba(255,255,255, 1);
    box-shadow: 0px 0 4px rgba(51, 51, 51, 0.3);
    max-width: 400px;
  }

  .info h2 {
    display: block;
    width: auto;
    font-size: 0.8rem;
    font-weight: 700;
    margin: 0;
  }

  .info span {
    display: inline-block;
    width: auto;
    margin: 0;
    font-size: 0.8rem;
  }

</style>
