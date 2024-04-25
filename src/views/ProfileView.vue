<script setup>
import { useRouter } from "vue-router";
import Corbado from "@corbado/web-js";
import { ref, onMounted } from "vue";

const user = ref(null);
const router = useRouter();

function redirectToHome() {
    router.push("/");
}

async function handleLogout() {
    user.value = null;
    await Corbado.logout();
    redirectToHome();
}

onMounted(() => {
    user.value = Corbado.user;
});

onMounted(() => {
    user.value = Corbado.user;
});
</script>

<template>
    <div>
        <div v-if="user">
            <h1>Profile Page</h1>
            <p>
                User-ID: {{ user.sub }}
                <br />
                Name: {{ user.name }}
            </p>
            <button @click="handleLogout">Logout</button>
        </div>

        <!-- Show the "not logged in" message if the user is not logged in -->
        <div v-else>
            <p>You're not logged in.</p>
            <p>
                Please go back to <a @click="redirectToHome">home</a> to log in.
            </p>
        </div>
    </div>
</template>
