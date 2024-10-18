<script setup lang="ts">
import { reactive, ref , Ref} from 'vue';
import type User from './types/User.ts';
import type Emoji from './types/Emoji.ts';
import TheHeader from '../src/components/TheHeader.vue';
import EntryEditor from '../src/components/EntryEditor.vue';
import EmojiField from './components/EmojiField.vue';

//Explicit Typing
const sum = (x: number, y: number) => {
    return x+y
}
//sum(5, "2") // not assignable to parameter number
console.log(sum(8,5))

//Typing reactive data
// import interface from types
const user: User = reactive({
    id: 1,
    username: "danielkellyio",
    settings:[]    
})
console.log(user)

//Typing Refs
//Inferred ref types take the first value assigned but for more complex refs it´s required to use Ref

const text = ref(""); // type inferred
//const emoji: Ref<Emoji|null> = ref();
//const emoji = ref<Emoji | null>(null);

//Typing


</script>

<template>
    <main class="container m-auto p-10">
        <TheHeader />
        <EntryEditor/>
        <EmojiField />
    </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>