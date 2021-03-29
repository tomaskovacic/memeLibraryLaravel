<template>
  <div>
    <div class="top-right links">
      <template v-if="authenticated">
         <router-link :to="{ name: 'welcome' }">
          {{ $t('home') }}
        </router-link>
        <router-link :to="{ name: 'home' }">
          {{ $t('Profile') }}
        </router-link>
         <router-link :to="{ name: 'post' }">
          {{ $t('Post Meme') }}
        </router-link>
      </template>
      <template v-else>
        <router-link :to="{ name: 'welcome' }">
          {{ $t('home') }}
        </router-link>
        <router-link :to="{ name: 'login' }">
          {{ $t('login') }}
        </router-link>
        <router-link :to="{ name: 'register' }">
          {{ $t('register') }}
        </router-link>
      </template>
    </div>

    <div class="text-center">
      <div class="title mb-4">
        {{ title }}
      </div>

      <div class="links">
        <b>Meme Library</b>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  layout: 'basic',

  metaInfo () {
    return { title: this.$t('home') }
  },

  data: () => ({
    title: window.config.appName
  }),

  computed: mapGetters({
    authenticated: 'auth/check'
  })
}
</script>

<style scoped>
.top-right {
  position: absolute;
  right: 10px;
  top: 18px;
}

.title {
  font-size: 85px;
}
</style>
