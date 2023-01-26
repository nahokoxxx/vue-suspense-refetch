<script setup lang="ts">
import { ref } from "vue";
import Person from "./components/Person.vue";

const ids = ref(["1", "5", "6"]);

function change() {
  ids.value = ["2", "3", "7"];
}
</script>

<template>
  <h1>The Star Wars People</h1>
  <button @click="change">Change People</button>
  <template v-for="id in ids">
    <Suspense timeout="0">
      <template #default>
        <Person :id="id" :key="id" />
      </template>
      <template #fallback>
        <div class="loading">Loading...</div>
      </template>
    </Suspense>
  </template>
</template>

<style scoped>
.people {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.loading {
  margin: 30px;
}
</style>
