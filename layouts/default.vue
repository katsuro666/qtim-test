<template>
  <div class="app">
    <LayoutHeader />

    <main>
      <NuxtPage />
    </main>

    <LayoutFooter />
  </div>
</template>

<style>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
main {
  flex-grow: 1;
}
</style>
