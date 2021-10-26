<template>
  <v-app>
    <v-app-bar app color="#F0F0F0" fixed light height="80px">
      <div class="app-title">
        Investment in Cryptocurrencies: Delegate to AI or not
      </div>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({
    //
  })
};
</script>

<style>
.app-title {
  font-size: 28px;
  font-weight: 500;
}
</style>
