<script setup>
import {toRefs} from 'vue'
import {ref} from 'vue'

const props = defineProps({
    dragonObject: {
        type: Object,
        required: true
    }
})

const newName = ref("")
const emit = defineEmits(["myCustomEvent"])

const {id, name, Skills, img_url} = toRefs(props.dragonObject)

// Functions

function emitSignal(){
    emit("myCustomEvent", "Her er en string fra dragon.vue!", id.value);
}

function handleSubmit() {
  if (newName.value.trim() === "") return
  emit("updateDragonName", { id: id.value, newName: newName.value })
  newName.value = ""
}

</script>

<template>
<article>
    <h3 @click="emitSignal">{{ name }}</h3>
    <p class="skills">{{ Skills }}</p>
    <img :src="img_url" alt="">
     <form @submit.prevent="handleSubmit">
    <label for="betterName">Rename to:</label>
    <input type="text" placeholder="Better name..." id="betterName" v-model="newName" required>
    <input type="submit" value="Update name" />
  </form>
</article>
</template>

<style scoped>
article {
    border: 2px solid red;
    border-radius: 6px;
    padding: 1rem;
        h3 {
            text-align: center;

        }
        img {
            max-width: 100%;
        }
}

form {
    display: flex;
    justify-content: space-between;
    align-items: center;

    input {
        border: 1px solid black;
        border-radius: 6px;
        padding: .5rem;
    }

    input[type="submit"] {
        background: red;
        color: white;
        border: none;
    }
}
</style>