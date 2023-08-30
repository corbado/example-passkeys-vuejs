<template>
  <corbado-auth :project-id="corbadoProjectID" conditional="yes">
    <input name="username" id="corbado-username" required autocomplete="webauthn"/>
  </corbado-auth>
</template>

<script setup>
import '@corbado/webcomponent/pkg/auth_cui.css'
import '@corbado/webcomponent'
import {ref} from 'vue'

const corbadoProjectID = ref(import.meta.env.VITE_CORBADO_PROJECT_ID)
</script>
