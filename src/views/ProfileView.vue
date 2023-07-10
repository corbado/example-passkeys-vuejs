<template>
  <div>
    <h1>Profile Page</h1>
    <div v-if="user">
      <p>
        User-ID: {{user.userID}}
        <br/>
        Email: {{user.email}}
      </p>
    </div>
    <button @click="handleLogout">Logout</button>
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
    const session = new Corbado.Session('pro-3280453392525787133');

    const handleLogout = () => {
      session.logout()
          .then(async () => {
            await router.push('/');
          })
          .catch(err => console.log(err))
    };

    onMounted(() => {
      session.refresh(u => {
        user.value = u;
      })
    });

    return {user, handleLogout}
  }
}
</script>