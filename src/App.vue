<script setup>
import { RouterView } from "vue-router";
import Corbado from "@corbado/web-js";
import { ref } from "vue";

const isInitialized = ref(false);

Corbado.load({
    projectId: import.meta.env.VITE_CORBADO_PROJECT_ID,
    darkMode: "on",
}).then(() => {
    isInitialized.value = true;
});
</script>

<template>
    <div v-if="isInitialized">
        <RouterView />
    </div>
</template>
