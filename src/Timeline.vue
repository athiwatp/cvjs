<template>
  <article>
    <h1>{{ title }}</h1>
    <ul class="timeline">
      <li v-for="item in items">
        <span>{{ item.start }} - {{ item.end }}</span>
        <h2 v-html="item.title"></h2>
        <h3>{{ item.subtitle }}</h3>
        <p>{{ item.description }}</p>
      </li>
    </ul>
  </article>
</template>

<script>
export default {
  props: ['items', 'title'],
  data () {
    return {}
  },
  computed: {},
  mounted () {},
  methods: {},
  components: {}
}
</script>

<style lang="css">
</style>
