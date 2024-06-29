<template>
  <div>
    <div class="my-3">
      <h1 class="font-weight-bold">{{ productC.title }}</h1>
    </div>
    <div class="card mb-3">
      <img
        :src="productC.image"
        class="card-img-top"
        :alt="productC.title"
        loading="lazy"
      />
      <div class="card-body">
        <h5 class="card-title">{{ productC.title }}</h5>
        <p class="card-text">{{ productC.description }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { params } = useRoute();
const productC = computed(() => product.value as IProduct);
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
const { data: product } = await useFetch(
  `https://fakestoreapi.com/products/${params.id}`
);
</script>

<style scoped>
.card img {
  height: 400px;
  object-fit: contain;
  object-position: center;
}
</style>
