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
        :total-amount="totalAmount"
        :amount="amount"
      >
        <template #chart> <ChartResume :amounts="amounts" /> </template>
        <template #action> <ActionHome @create="create" /> </template>
      </IndexHome>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove" />
    </template>
  </Layout>
</template>

<script>
import Layout from './LayoutHome.vue'
import HeaderHome from './HeaderHome.vue'
import IndexHome from './Resume/IndexResume.vue'
import Movements from './Movements/IndexMovements.vue'
import ActionHome from './ActionHome.vue'
import ChartResume from './Resume/ChartResume.vue'

export default {
  components: {
    Layout,
    HeaderHome,
    IndexHome,
    Movements,
    ActionHome,
    ChartResume
  },
  data() {
    return {
      amount: null,
      label: null,
      movements: []
    }
  },
  computed: {
    amounts() {
      const lastDays = this.movements
        .filter((m) => {
          const today = new Date()
          const oldDate = today.setDate(today.getDate() - 30)
          return m.time > oldDate
        })
        .map((m) => m.amount)

      return lastDays.map((m, i) => {
        const lastMovements = lastDays.slice(0, i)
        return lastMovements.reduce((suma, movement) => {
          return suma + movement
        }, 0)
      })
    },
    totalAmount() {
      return this.movements.reduce((suma, m) => {
        return suma + m.amount
      }, 0)
    }
  },
  mounted() {
    const movements = JSON.parse(localStorage.getItem('movements'))
    console.log(movements)
    if (Array.isArray(movements)) {
      this.movements = movements.map((m) => {
        return { ...m, time: new Date(m.time) }
      })
    }
  },
  methods: {
    create(movement) {
      this.movements.push(movement)
      this.save()
    },
    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id)
      this.movements.splice(index, 1)
      this.save()
    },
    save() {
      localStorage.setItem('movements', JSON.stringify(this.movements))
    }
  }
}
</script>
