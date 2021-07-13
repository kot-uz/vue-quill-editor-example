<template>
  <div>
    <quill-editor @savePost="savePost" />
    <div class="posts">
      <div v-for="post in posts" :key="post.id">
        <post :id="post.id" :text="post.text" />
      </div>
    </div>
  </div>
</template>

<script>
import QuillEditor from "../components/QuillEditor.vue";
import Post from "@/components/Post.vue";

export default {
  components: {
    QuillEditor,
    Post,
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    savePost(post) {
      console.log("Posts.vue -> savePost", post);
      const newPost = { id: +new Date(), text: post };
      this.posts.push(newPost);
    },
  },
};
</script>

<style scoped>
.posts {
  padding: 10px;
}
</style>
