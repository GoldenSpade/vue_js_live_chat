<template>
  <div class="container">
    <Navbar />
    <ChatWindow />
    <NewChatForm />
  </div>
</template>
<script>
import NewChatForm from '@/components/NewChatForm'
import ChatWindow from '@/components/ChatWindow'
import Navbar from '@/components/Navbar'

import getUser from '@/composables/getUser'
import {watch} from 'vue'
import {useRouter} from 'vue-router'

export default {
  components: {Navbar, NewChatForm, ChatWindow},

  setup() {
    const {user} = getUser()
    const router = useRouter() 

    watch(user, () => {
      if (!user.value) {
        router.push({name: 'Welcome'})
      }
    })

    return {
      user,
      router,
    }
  },
}
</script>
<style>
</style>