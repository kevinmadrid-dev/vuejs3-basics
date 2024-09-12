<template>
  <div class="post-card">
    <h3>Título</h3>

    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum atque eveniet
      ad ut quam iste nostrum fugiat qui laboriosam autem praesentium dignissimos
      nam, odio adipisci sed? Minima laudantium ex mollitia?
    </p>

    <PostButton />
  </div>
</template>

<script lang="ts" setup>
import PostButton from "./PostButton.vue"
</script>

<style scoped>
.post-card {
  border-radius: 15px;
  padding: 10px;
  margin: 5px;
  border: 1px solid #ccc;
}
</style>
