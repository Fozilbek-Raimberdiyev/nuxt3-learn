<template>
  <div class="">
    <div class="my-3">
      <h1 class="font-weight-bold">Bosh sahifa</h1>
    </div>
    <div class="row g-3">
      <div
        v-for="photo in productsC"
        :key="photo.id"
        class="col-4 position-relative"
      >
        <NuxtLink
          :to="`/products/${photo.id}`"
          class="text-decoration-none text-dark"
        >
          <div class="card h-100">
            <img
              :src="photo.image"
              class="card-img-top"
              :alt="photo.title"
              loading="lazy"
            />
            <div class="card-body">
              <h4 class="card-title">{{ photo.title }}</h4>
              <p class="card-text">{{ photo.description }}</p>
            </div>
          </div>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
interface IProduct {
  id: number;
  title: string;
  price: number;
  description: string;
  category: string;
  image: string;
  rating: {
    rate: number;
    count: number;
  };
}

const productsC = computed(() => products.value as IProduct[]);

const { data: products } = await useAsyncData("photos", async () => {
  const res = await fetch("https://fakestoreapi.com/products");
  const resJson = await res.json();
  return resJson;
  //   return $fetch("https://jsonplaceholder.typicode.com/photos");
});

useSeoMeta({
  title: "Bosh sahifa",
  ogTitle: "Bosh sahifa",
  description: "Nuxt 3 minimal starter",
  ogDescription: "Nuxt 3 minimal starter",
  ogImage: "https://nuxtjs.org/social.png",
});
</script>

<style scoped>
.card img {
  height: 300px;
  object-fit: contain;
  object-position: center;
}
</style>
