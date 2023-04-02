<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layout>
    <template #header>
      <HeaderHome/>
    </template>
    <template #resume>
      <IndexHome/>
    </template>
    <template #movements>
      <Movements/>
    </template>
  </Layout>
</template>

<script>
import Layout from './LayoutHome.vue'
import HeaderHome from './HeaderHome.vue'
import IndexHome from './Resume/IndexHome.vue'
import Movements from './MovementsHome.vue'

export default {
  components: {
    Layout,
    HeaderHome,
    IndexHome,
    Movements
  }
}
</script>
