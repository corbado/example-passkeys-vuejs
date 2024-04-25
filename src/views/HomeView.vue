<script setup>
import { onMounted, ref } from "vue";
import Corbado from "@corbado/web-js";
import { useRouter } from "vue-router";

const router = useRouter();
const authElement = ref(null);

if (Corbado.isAuthenticated) {
    router.push("/profile");
}

onMounted(() => {
  Corbado.mountAuthUI(authElement.value, {
    onLoggedIn: () => {
      router.push("/profile");
    },
    isDevMode: true,
  });
});
</script>

<template>
    <div ref="authElement"></div>
</template>
