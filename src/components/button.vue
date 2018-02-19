<template>

  <div>
    <button :disabled="!hasUser" @click="mudarDados">Mudar dados do usuário</button>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
  export default {
    methods: {
      mudarDados() {
        const payload = {
          name: 'Outro nome',

          email: 'outro@email.com',

          level: 'usuario-simples',

          city: 'Abaetetuba',

          state: 'PA'
        }

        this.changeUser(payload)

      },

      ...mapActions(['changeUser'])
    },
    computed: {
      hasUser () {
        return this.$store.state.user.name !== ''
      }
    }
  }
</script>
