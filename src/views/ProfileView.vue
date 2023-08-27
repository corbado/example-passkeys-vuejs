<template>
  <div>
    <div v-if="user">
      <h1>Profile Page</h1>
      <p>
        User-ID: {{ user.userID }}
        <br/>
        Email: {{ user.email }}
      </p>
      <button @click="handleLogout">Logout</button>
    </div>

    <!-- Show the "not logged in" message if the user is not logged in -->
    <div v-else>
      <p>You're not logged in.</p>
      <p>Please go back to <a @click="redirectToHome">home</a> to log in.</p>
    </div>
  </div>
</template>

<script>
import Corbado from '@corbado/webcomponent';
import {ref, onMounted} from 'vue'
import {useRouter} from 'vue-router'

export default {
  setup() {
    const router = useRouter();
    const user = ref(null);
    const session = new Corbado.Session(import.meta.env.VITE_CORBADO_PROJECT_ID);

    const handleLogout = () => {
      session.logout()
          .then(async () => {
            await router.push('/');
          })
          .catch(err => console.log(err))
    };

    const redirectToHome = () => {
      router.push('/');
    }


    onMounted(() => {
      session.refresh(u => {
        user.value = u;
      })
    });

    return {user, handleLogout, redirectToHome}
  }
}
</script>