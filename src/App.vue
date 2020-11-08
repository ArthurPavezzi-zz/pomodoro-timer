<template>
  <div id="app">
    <Home/>
  </div>
</template>

<script>
import Home from "@/views/Home";

import i18n from "./i18n.js"
i18n.locale = "en"

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>