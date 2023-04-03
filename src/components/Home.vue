<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <Layout>
    <template #header>
      <HeaderHome />
    </template>
    <template #resume>
      <IndexHome
        :total-label="'Ahorro Total'"
        :label="label"
        :total-amount="100000"
        :amount="amount"
      >
        <template #chart> chart </template>
        <template #action> action </template>
      </IndexHome>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>

<script>
import Layout from './LayoutHome.vue'
import HeaderHome from './HeaderHome.vue'
import IndexHome from './Resume/IndexResume.vue'
import Movements from './Movements/IndexMovements.vue'

export default {
  components: {
    Layout,
    HeaderHome,
    IndexHome,
    Movements
  },
  data() {
    return {
      amount: null,
      label: null,
      movements: [
        {
          id: 0,
          title: 'Movimiento 1',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 1,
          title: 'Movimiento 2',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 2,
          title: 'Movimiento 3',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 3,
          title: 'Movimiento 4',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 4,
          title: 'Movimiento 5',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 5,
          title: 'Movimiento 6',
          description: 'Loremsadd asdaas',
          amount: 1000
        },
        {
          id: 6,
          title: 'Movimiento 7',
          description: 'Loremsadd asdaas',
          amount: 1000
        }
      ]
    }
  }
}
</script>

<style scoped>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
