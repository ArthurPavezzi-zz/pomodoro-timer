<template>
  <v-footer dark padless>
    <v-card flat tile class="red lighten-1 white--text text-center">
      <v-row justify="center" no-gutters>
        <v-btn v-for="link in links" :key="link.name" color="white" text rounded class="my-2">
          <a :href="link.href">{{ link.name }}</a>
        </v-btn>
      </v-row>
      <v-divider></v-divider>
      <v-card flat tile class="red lighten-1 white--text text-center authorship">
        Made with ♥ by <a href="https://github.com/ArthurPavezzi">Arthur Pavezzi</a>
      </v-card>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      links: [
        {
          name: 'Home',
          href: '/'
        },
        {
          name: 'Contact',
          href: 'mailto:arthur.henrique.pavezzi@gmail.com'
        }
      ]
    }
  }
}
</script>

<style lang="sass" scoped>
.v-card
  width: 100vw
  //padding: 20px 0 0 0

  a
    text-decoration: none
    color: whitesmoke

.authorship
  padding: 10px 0
  font-size: 14px
</style>