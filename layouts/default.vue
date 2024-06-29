<template>
  <header>
    <!-- Nav tabs -->
    <ul class="nav nav-tabs" id="navId">
      <li class="nav-item">
        <NuxtLink to="/" class="nav-link">Bosh sahifa</NuxtLink>
      </li>
      <li class="nav-item dropdown" v-if="false">
        <a
          class="nav-link dropdown-toggle"
          data-toggle="dropdown"
          href="#"
          role="button"
          aria-haspopup="true"
          aria-expanded="false"
          >Dropdown</a
        >
        <div class="dropdown-menu">
          <a class="dropdown-item" href="#tab2Id">Action</a>
          <a class="dropdown-item" href="#tab3Id">Another action</a>
          <div class="dropdown-divider"></div>
          <a class="dropdown-item" href="#tab4Id">Action</a>
        </div>
      </li>
      <li class="nav-item">
        <NuxtLink to="/data-fetching" class="nav-link">Todos</NuxtLink>
      </li>
      <li class="nav-item" v-if="false">
        <a href="#" class="nav-link disabled">Disabled</a>
      </li>
    </ul>

    <!-- Tab panes -->
    <div class="tab-content">
      <div class="tab-pane fade show active" id="tab1Id" role="tabpanel"></div>
      <div class="tab-pane fade" id="tab2Id" role="tabpanel"></div>
      <div class="tab-pane fade" id="tab3Id" role="tabpanel"></div>
      <div class="tab-pane fade" id="tab4Id" role="tabpanel"></div>
      <div class="tab-pane fade" id="tab5Id" role="tabpanel"></div>
    </div>
  </header>
  <main class="container">
    <NuxtPage></NuxtPage>
  </main>
</template>

<script setup lang="ts"></script>

<style scoped>
.router-link-active,
.router-link-exact-active {
  color: var(--bs-nav-tabs-link-active-color);
  background-color: var(--bs-nav-tabs-link-active-bg);
  border-color: var(--bs-nav-tabs-link-active-border-color);
}
</style>
