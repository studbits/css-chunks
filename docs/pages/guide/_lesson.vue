<template>
  <div>
    <ul>
      <li v-for="lesson in menu">
        <nuxt-link :to="lesson.slug"> {{ lesson.heading }} </nuxt-link>
      </li>
    </ul>
    <comonent :is="currentLesson" />
  </div>
</template>

<script>
import docs from '~documentation/index'
import compsToMenu, { toHeading } from '~utilities/menu'

export default {
  data({ route }) {
    return {
      currentLesson: route.params.lesson || 'Introduction'
    }
  },

  head() {
    return {
        title: toHeading(this.currentLesson) + ' - Vuency'
    }
  },

  created() {
    this.menu = compsToMenu(docs)
  },

  components: docs
}
</script>
