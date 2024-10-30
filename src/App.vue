<script setup lang="ts">
import CardView from './components/CardView.vue'
</script>
<template>
  <main>
    <header id="header-app">
      <div>Todo List App</div>
    </header>
    <card-view />
  </main>
</template>

<style scoped>
* {
  box-sizing: border-box;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

#header-app{
  padding: 20px;
  color: #f4f6ff;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: larger;
  font-weight: bold;
}
</style>
