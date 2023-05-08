<script setup>
import { ref } from 'vue';
import Chatbot from '../../components/Chatbot.vue';

const dropdownItems = ref([
    { name: 'Option 1', code: 'Option 1' },
    { name: 'Option 2', code: 'Option 2' },
    { name: 'Option 3', code: 'Option 3' }
]);

const dropdownItem = ref(null);
</script>

<script>
export default {
    name: 'ChatGPT3.5',
    components: { Chatbot },
    data() {
        return {};
    }
};
</script>

<template>
    <Chatbot />
    <!-- <div class="grid p-fluid">
        <Chatbot />
    </div> -->
</template>
