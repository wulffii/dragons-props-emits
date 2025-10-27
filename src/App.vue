<script setup>
import { ref} from 'vue';
import dragonData from "./assets/js/dragons"
import dragonComp from './components/dragonComp.vue';

// STATE

const dragons = ref(dragonData)

// FUNCTION

function handleEmit(textMsg, dragonId) {
  console.log(textMsg, dragonId)
}

function updateDragonName({ id, newName }) {
  const dragon = dragons.value.find(d => d.id === id)
  if (dragon) {
    dragon.name = newName
  }
}
</script>

<template>

  <!--  -->
  <!-- Del 2: emits -->
  <!--  -->

  <!-- 16. Ekstra/evt: lav en mulighed for at delete dragerne i DragonComp. Så de sender en anden custom event og App.vue fjerner den relevante drage fra state - hjælp i de kommende trin. Se her: https://youtu.be/uXvypD2gPjw -->

  <!-- 17. Opsæt en deleteknap og opsæt eventlistener på den der kalder en funktion: handleDelete -->

  <!-- 18. handleDelete skal emitte en custom event (deleteDragon) OG sende dragens ID som payload -->

  <!-- 19. I app.vue skal DragonComp nu lytte efter deleteDragon eventet og håndtere dette. Den skal bruge id'et fra den drage der skal slettes og slette den rigtige drage i listen med drager i state i App.vue. Her kan man anvende .filter() metoden -->

  <header>
    <h1>D&D website</h1>
    <h2>
      Your source for DnD dragons. Providing dragon information since 2021.<br />
      Find info about <span>{{ dragons.length }}</span> dragons here.
    </h2>
  </header>
  <main>
    <dragonComp @myCustomEvent="handleEmit" @updateDragonName="updateDragonName" v-for="dragon in dragons" :key="dragon.id" :dragonObject="dragon"/>
  </main>
</template>

<style scoped>
header {
  text-align: center;
  min-height: 60vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.9)),
    url("@/assets/img/bg_dragon.jpg");
  background-size: cover;
  display: grid;
  place-content: center;
  color: white;
}

h1 {
  font-size: 4rem;
}

span {
  color: crimson;
}

main {
  max-width: 1000px;
  margin: 1rem auto;
  padding: 2rem;
  box-shadow: 0 0 3px 1px rgba(0, 0, 0, 0.3);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  border-radius: 6px;
}

@media screen and (max-width: 1050px) {
  main {
    grid-template-columns: 1fr;
    padding: 5rem;
  }
}
</style>
