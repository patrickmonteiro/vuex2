<template>
  <div>
    <h1>Welcome Vue2</h1>
    <h4>{{ user }}</h4>
    <hr>
    <cc-users></cc-users>
  </div>
</template>

<script>
import CcUsers from './components/users/main'

import { mapState, mapActions } from 'vuex'
  export default {
    name: 'CodeCastsApp',
    mounted () {
      const payload = {
          name: 'Patrick Monteiro',

          email: 'eng.patrickmonteiro@gmail.com',

          level: 'usuario-master',

          city: 'Belém',

          state: 'SP',
        }
        setTimeout(() => {
          this.changeUser(payload)
          // this.$store.dispatch('changeUser', payload)
          // this.$store.commit('CHANGE_USER', payload)
        } ,3000)
    },
    components: {
      CcUsers
    },
    methods: {
      ...mapActions(['changeUser']) 
    },
    computed: {
      ...mapState({
        user: state => {
          const { name, email } = state.user
          return `O usuário logado é ${name} e possui o email ${email}`
        }
      })
      // user () {
      //   const { name, email } = this.$store.state.user
      //   return `O usuário logado é ${name} e possui o email ${email}`
      // }
    }
  }
</script>