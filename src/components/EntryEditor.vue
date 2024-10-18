<script lang="ts" setup>
import EmojiField from "./EmojiField.vue";
import type Emoji from "../types/Emoji";
import { ref, computed} from "vue";

const props = defineProps<{
    user?: {
        username: string;
        required:true
    }
}>();


//Typing refs
const text= ref("") // type inferred

//const emoji: Ref<Emoji|null> = ref();
const emoji = ref<Emoji | null>(null);// Reactive reference with a valid Emoji o null value

//Typing computed
const charCount = computed(() => text.value.length);

const maxChars = 280;

//Typing Events
const handleTextInput = (e: Event) =>{
    const textarea = e.target as HTMLTextAreaElement; // cuadno va a obtener el valor del area de texto
    //console.log(textarea.value);
    if(textarea.value.length <= maxChars){
        text.value = textarea.value
    } else{
        text.value = textarea.value = textarea.value.substring(0,maxChars)

    }

} ;


</script>
<template>
    <form class="entry-form" @submit.prevent="$emit('create', {text,emoji})">
    <textarea
        :value="text"
        @keyup="handleTextInput"
        :placeholder="`New Journal Entry for @daniellKelly`"
    ></textarea>
        <EmojiField v-model="emoji" />
        <div class="entry-form-footer">
            <span>{{ charCount }} / {{ maxChars }}</span>
            <button>Remember</button>
        </div>
    </form>
</template>

<style scoped>
.entry-form{
    

}
.entry-form-footer{


}

</style>/