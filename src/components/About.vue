<template>
  <v-main id="about">
    <v-row>
      <v-col sm="7" offset-sm="3">
        <h2>{{ $t('about.h2' ) }}</h2>
        <h3>{{ $t('about.what.h3') }}</h3>
        <p>{{ $t('about.what.citation') }}
          <a :href="$t('about.what.href')">{{ $t('about.what.wiki') }}</a>
        </p>
        <h3>{{ $t('about.howTo.h3') }}</h3>
        <ol type="1">
          <li><b>{{ $t('about.howTo.list.1.b') }}</b> {{ $t('about.howTo.list.1.normal') }}</li>
          <li><b>{{ $t('about.howTo.list.2.b') }}</b> {{ $t('about.howTo.list.2.normal') }}</li>
          <li><b>{{ $t('about.howTo.list.3.b') }}</b> {{ $t('about.howTo.list.3.normal') }}</li>
          <li><b>{{ $t('about.howTo.list.4.b') }}</b> {{ $t('about.howTo.list.4.normal') }}</li>
          <li><b>{{ $t('about.howTo.list.5.b') }}</b> {{ $t('about.howTo.list.5.normal') }}</li>
        </ol>
        <h3>{{ $t('about.features.title') }}</h3>
        <ul>
          <li><b>{{ $t('about.features.1.b') }}</b> {{ $t('about.features.1.normal') }}</li>
          <li><b>{{ $t('about.features.2.b') }}</b> {{ $t('about.features.2.normal') }}</li>
          <li><b>{{ $t('about.features.3.b') }}</b> {{ $t('about.features.3.normal') }}</li>
        </ul>
      </v-col>
    </v-row>
  </v-main>
</template>

<script>
export default {
name: "About"
}
</script>

<style lang="sass" scoped>
#about
  background-color: whitesmoke
  margin: 0 auto

h2
  margin: 20px 0

h3
  margin: 20px 0 10px 0
  &::after
    content: ''
    border-bottom: 3px solid #F05B56
    width: 10px
    display: block

p a
  color: #F05B56
  text-decoration: none
</style>