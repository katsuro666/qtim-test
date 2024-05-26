<template>
  <div class="loader" v-if="post.description.length === 0">Loading...</div>

  <div v-else class="post__container">
    <h1 class="post__heading">{{ post.preview }}</h1>

    <img :src="post.image" alt="Post image" class="post__image" />

    <div class="post__about">
      <span class="about__tip">About</span>
      <p class="about__text">{{ post.description }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios';

interface Post {
  preview: string;
  description: string;
  image: string;
}

const post = ref<Post>({
  preview: '',
  description: '',
  image: '',
});
const route = useRoute();
const postID = ref(route.params.post);

const fetchPost = async () => {
  try {
    const response = await axios.get(
      `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${postID.value}`
    );
    post.value = response.data;
  } catch (error) {
    console.error('Error fetching posts:', error);
  }
};

onMounted(() => {
  fetchPost();
});
</script>

<style lang="scss" scoped>
.loader {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.post__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 119px 112px 80px;
}

.post__heading {
  font-size: 84px;
  font-weight: 400;
  margin: 0;
}

.post__image {
  width: 100%;
  margin: 73px auto 80px;
}

.post__about {
  width: 695px;
  align-self: baseline;
}

.about__tip {
  font-size: 16px;
}

.about__text {
  font-size: 36px;
  margin: 32px 0 0;
}
</style>
