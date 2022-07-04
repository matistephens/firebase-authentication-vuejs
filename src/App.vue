<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div
        class="d-flex align-center"
        @click="$router.push('/')"
        style="cursor: pointer"
      >
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://www.gstatic.com/mobilesdk/160503_mobilesdk/logo/2x/firebase_28dp.png"
          transition="scale-transition"
          width="40"
        />

      </div>

      <SignInBtn v-if="!activeLogin" />
      <SignOutBtn v-if="activeLogin" />
      <SignUpBtn v-if="!activeLogin" />

      <v-spacer></v-spacer>

    </v-app-bar>

    <v-main>
      <v-container>
        <router-view />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import SignInBtn from '@/components/SignInBtn.vue';
import SignOutBtn from '@/components/SignOutBtn.vue';
import SignUpBtn from "@/components/SignUpBtn.vue";
 
import { mapGetters } from 'vuex';

export default {
  name: 'App',
  components: { SignInBtn, SignOutBtn, SignUpBtn },
  data: () => ({}),
  computed: {
    ...mapGetters('session', ['activeLogin']),
  },
  mounted() {
    this.$store.dispatch('session/subscribeToAuthStateChange');
  },
};
</script>
