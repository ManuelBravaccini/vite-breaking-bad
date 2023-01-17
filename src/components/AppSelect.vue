<script>
import { store } from "../store.js";

export default {
  name: "AppSelect",
  data() {
    return {
      store,
      archetypes: ['Alien', 'Laval', 'Vylon', 'Inzektor', 'Umi', 'Gusto'],
    };
  },
};
</script>

<template>
  <div>
    <select v-model="store.archetype">
      <!--
      <option value="">(Select archetype)</option>
      -->
      <option v-for="(archetypeEl, index) in archetypes" :key="index" :value="archetypeEl">
        {{ archetypeEl }}
      </option>
    </select>
  </div>
</template>

<style  lang="scss" scoped>
select {
  margin: 1rem 5rem;
  padding: .5rem;
  border-radius: 5px;
  font-size: 1rem;
}
</style>
