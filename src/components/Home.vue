<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layout>
    <template #header>
      <HeaderHome></HeaderHome>
    </template>
  </Layout>
</template>

<script>
import Layout from './LayoutHome.vue'
import HeaderHome from './HeaderHome.vue'

export default {
  components: {
    Layout,
    HeaderHome
  }
}
</script>
