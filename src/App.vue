<script setup></script>

<template>
  <!--  -->
  <!-- Del 1: props -->
  <!--  -->

  <!-- 0. Se filer igennem og forstå opbygning, hvor kommer styling fra (global, lokal) osv -->

  <!-- 1. Importer dragerne og gem dem i state (reactive state...hvad skal vi huske at importere for at gøre data reactive?) - de ligger i assets/dragons.js -->

  <!-- 2. I App.vue i <h2> sørg for tallen indsættes dynamisk: se eksempel her: https://prnt.sc/XTygZonF7YCX -->

  <!-- 3. Lav nu en childcomponent: DragonComp.vue inde i "assets/components"-mappen -->

  <!-- 4. Importér din nye childcomponent i App.vue -->

  <!-- 5. Loop igennem state med listen af drager og lav en DragonComp for hver -->

  <!-- 6. Send "dragedata" fra App.vue NED til dine childcomponents - send alt data, det vil sige send drage-objektet -->

  <!-- 7. I DragonComp skal I nu modtage props fra App.vue. Herefter skal I anvende dette og bygge en simpel template til dragerne, de skal som minimum indeholde id, name, Skills og vise billedet af dragen. OBS: for at "hive" data ud af props kan I:
   - Gøre på den mest kedelige og usexede måde: 
      <p>Den her drage hedder {{ props.dragonProps.name }} og er {{ props.dragonPoops.age }}</p>

   - Gøre det med destructuring: 
      const {name, age} = props.dragonProps
      <p>Den her drage hedder {{ name }} og er {{ age }}</p>

   - Gøre det på den FEDE måde hvor vi hiver reactive props ud (selvom vi ikke skal bruge det til noget her...):
      import {toRefs} from "vue"; //https://vuejs.org/api/reactivity-utilities.html#torefs
      const {name, age} = toRefs(props.dragonProps)
      <p>Den her drage hedder {{ name }} og er {{ age }}</p>
  -->

  <!-- 8. I skal nu gøre klar til noget vi skal bruge senere. Indsæt følgende nederst i DragonComp:  
  <form>
    <label for="betterName">Rename to:</label>
    <input type="text" placeholder="Better name..." id="betterName" required>
    <input type="submit" value="Update name" />
  </form> -->

  <!-- 9. Style det grundlæggende, men brug IKKE for lang tid på styling, det KUNNE se sådan her ud: https://prnt.sc/spZH-GvZ4r5E -->

  <!-- 10. Anvend til sidst v-model til at binde text-input feltet til en reaktiv variabel (state) som du skal lave, kald den f.eks. newName -->

  <!--  -->
  <!-- Del 2: emits -->
  <!--  -->

  <!-- 11. Opsæt nu en eventlistener på formularen i DragonComp der lytter efter submit som kører en funktion "handleSubmit" -->

  <!-- 12. Lav handleSumbit og sørg for at den emitter en custom-event der hedder f.eks. "updateName" - sørg for at DragonComp "ved" at I vil emitte...hvordan fortæller man den det? Selve funktionen behøver i FØRSTE omgang ikke gøre andet end at emitte -->

  <!-- 13. Lyt nu denne custom event i App.vue og kald en funktion når den indtræder, log til konsol i denne funktion -->

  <!-- 14. Udbyg nu DragonComp til at sende det nye navn (newName ref'en vi lavede i step 10) SAMT dragens id i payload i handleSubmit -->

  <!-- 15. Modtag nu payload(s) i App.vue og log dem -->

  <!-- 16. Udbyg nu i App.vue så:
        - Den korrekte drage findes ud fra det id der er sendt i payload (anvend .find(): https://www.w3schools.com/jsref/jsref_find.asp)
        - Denne drages name skal nu opdateres med det name der er sendt i payload fra DragonComp
  -->

  <!-- 17. Ekstra/evt: lav en mulighed for at delete dragerne i DragonComp. Så de sender en anden custom event og App.vue fjerner den relevante drage fra state. Se her: https://youtu.be/uXvypD2gPjw -->

  <header>
    <h1>D&D website</h1>
    <h2>
      Your source for DnD dragons. Providing dragon information since 2021.<br />
      Find info about <span>8</span> dragons here.
    </h2>
  </header>
  <main>
    <!-- Indsæt drager her... -->
  </main>
</template>

<style scoped>
header {
  text-align: center;
  min-height: 60vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.9)), url("@/assets/img/bg_dragon.jpg");
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
