<template>
  <div>
    <div class="my-3">
      <h1 class="font-weight-bold">Data fetching</h1>
    </div>
    <div class="row g-3" v-if="!isLoading && todos">
      <div v-for="todo in todos" :key="todo.id" class="col-4 position-relative">
        <div class="card h-100">
          <div class="card-body">
            <h5 class="card-title">{{ todo.title }}</h5>
            <div class="d-flex justify-content-between align-items-center">
              <p class="card-text">Bajarilish holati</p>
              <input
                type="checkbox"
                :checked="todo.completed"
                :disabled="true"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="text-primary d-flex justify-content-center align-items-center text-center my-5"
      role="status"
      v-else-if="isLoading"
    >
      <div class="spinner-border"></div>
    </div>
    <div class="text-center" v-else>
      <h3>Ma'lumotlar yuklanmadi</h3>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
interface ITodo {
  userId: number;
  id: number;
  title: string;
  completed: boolean;
}
const todos = ref<ITodo[]>([]);
const isLoading = ref(false);
async function fetchTodos() {
  try {
    isLoading.value = true;
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    todos.value = await response.json();
    isLoading.value = false;
  } catch (e) {
    isLoading.value = false;
  }
}

fetchTodos();
</script>

<style scoped></style>
