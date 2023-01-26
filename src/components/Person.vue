<script setup lang="ts">
type Props = {
  id: string;
};

const props = defineProps<Props>();

const response = await fetch(`https://swapi.dev/api/people/${props.id}`);
const person = await response.json();
</script>

<template>
  <div>
    <h2>{{ person.name }}</h2>
    <div>Gender: {{ person.gender }}</div>
    <div>Hair Color: {{ person.hair_color }}</div>
  </div>
</template>
