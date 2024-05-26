<template>
  <div class="loader" v-if="!posts.length">Loading...</div>

  <template v-if="posts.length">
    <div class="posts__container" v>
      <NuxtLink :to="`/posts/${post.id}`" v-for="post in displayedPosts" :key="post.id" class="link">
        <div class="post">
          <img :src="post.image" alt="Post image" class="post__image" />
          <p class="post__title">{{ post.preview }}</p>
          <span class="post__read-more">Read more</span>
        </div>
      </NuxtLink>
    </div>

    <div class="pagination">
      <button
        @click="prevPage"
        v-if="currentPage !== 1"
        class="pagination__button--arrow pagination__button--arrow-back btn">
        <
      </button>
      <button
        v-for="page in paginationRange"
        @click="currentPage = page"
        :key="page"
        class="pagination__button btn"
        :class="{ 'pagination__button--active': currentPage === page }">
        {{ page }}
      </button>
      <button
        @click="nextPage"
        v-if="currentPage !== totalPages"
        class="pagination__button--arrow pagination__button--arrow-forward btn">
        >
      </button>
    </div>
  </template>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted } from 'vue';
import axios from 'axios';

interface Post {
  id: number;
  preview: string;
  image: string;
}

const posts = ref<Post[]>([]);
const currentPage = ref(1);
const postsPerPage = 8;

const fetchPosts = async () => {
  try {
    const response = await axios.get('https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/');
    posts.value = response.data;
  } catch (error) {
    console.error('Error fetching posts:', error);
  }
};

const paginationRange = computed(() => {
  const startPage = Math.max(currentPage.value - 2, 1);
  const endPage = Math.min(currentPage.value + 2, totalPages.value);

  let pages = [];
  for (let page = startPage; page <= endPage; page++) {
    pages.push(page);
  }

  return pages;
});

const displayedPosts = computed(() => {
  const start = (currentPage.value - 1) * postsPerPage;
  const end = start + postsPerPage;
  return posts.value.slice(start, end);
});

const totalPages = computed(() => {
  return Math.ceil(posts.value.length / postsPerPage);
});

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

onMounted(() => {
  fetchPosts();
});
</script>

<style lang="scss" scoped>
.loader {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 1000px;
  width: 100%;
}
.posts__container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 40px 32px;
}

.link {
  color: inherit;
  text-decoration: none;
}
.post {
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: all ease 0.3s;

  &:hover {
    cursor: pointer;
    transform: translateY(-20px);

    .post__read-more {
      display: block;
    }
  }
}
.post__image {
  width: 280px;
  height: 280px;
  object-fit: cover;
}
.post__title {
  margin: 24px 0 12px;
  padding: 0;
  font-size: 20px;
  height: 72px;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}

.pagination {
  position: relative;
  display: flex;
  gap: 8px;
  align-items: center;
  margin-top: 50px;
}

.pagination__button {
  border: none;
  background: $gray-1;
  color: $dark-1;

  &--active {
    background: $dark-1;
    color: #ffffff;
  }

  &--arrow {
    background-color: transparent;
    border: 1px solid $gray-1;
    color: $gray-500;

    &-back {
      position: absolute;
      left: -52px;
    }
  }
}

.btn {
  width: 44px;
  height: 44px;
  border-radius: 12px;

  &:hover {
    cursor: pointer;
  }
}

.post__read-more {
  display: none;
  position: absolute;
  bottom: -12px;
  align-self: baseline;
  font-size: 20px;
  color: $footer-bg;
}
</style>
