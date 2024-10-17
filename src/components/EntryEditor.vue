<script lang="ts" setup>
import EmojiField from "./EmojiField.vue";
import type Emoji from "../types/Emoji";
import { ref, computed} from "vue";

const props = defineProps<{
    user: {
        username: string;
        required:true
    }
}>();

const maxChars = 280;

//Typing refs
const text= ref("") // type inferred

//const emoji: Ref<Emoji|null> = ref();
const emoji = ref<Emoji | null>(null);// Reactive reference with a valid Emoji o null value

//Typing computed
const charCount = computed(() => text.value.length);

//Typing events
const handleTextInput=(e:Event)=>{
    const textarea = e.target
    console.log(textarea)
}

</script>
<template>
    <form class="entry-form" @submit.prevent="handleSubmit">
    <textarea
        :value="text"
        @keyup="handleTextInput"
        :placeholder="`New Journal Entry for ${props.user.username || 'anonymous'}`"
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