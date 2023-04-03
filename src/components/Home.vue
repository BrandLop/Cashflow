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
        <template #chart> <ChartResume :amounts="amounts" /> </template>
        <template #action> <ActionHome @create="create" /> </template>
      </IndexHome>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove"/>
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
      movements: [
        {
          id: 0,
          title: 'Movimiento 1',
          description: 'Lorem ipsum dolor sit amet',
          amount: 100,
          time: new Date('28 Mar 2023')
        },
        {
          id: 1,
          title: 'Movimiento 2',
          description: 'Lorem ipsum dolor sit amet',
          amount: 200,
          time: new Date('27 Mar 2023')
        },
        {
          id: 2,
          title: 'Movimiento 3',
          description: 'Lorem ipsum dolor sit amet',
          amount: 500,
          time: new Date('26 Mar 2023')
        },
        {
          id: 3,
          title: 'Movimiento 4',
          description: 'Lorem ipsum dolor sit amet',
          amount: 200,
          time: new Date('25 Mar 2023')
        },
        {
          id: 4,
          title: 'Movimiento 5',
          description: 'Lorem ipsum dolor sit amet',
          amount: -400,
          time: new Date('24 Mar 2023')
        },
        {
          id: 5,
          title: 'Movimiento 6',
          description: 'Lorem ipsum dolor sit amet',
          amount: -600,
          time: new Date('23 Mar 2023')
        },
        {
          id: 6,
          title: 'Movimiento 7',
          description: 'Lorem ipsum dolor sit amet',
          amount: -300,
          time: new Date('22 Mar 2023')
        },
        {
          id: 7,
          title: 'Movimiento 8',
          description: 'Lorem ipsum dolor sit amet',
          amount: 100,
          time: new Date('21 Mar 2023')
        },
        {
          id: 8,
          title: 'Movimiento 9',
          description: 'Lorem ipsum dolor sit amet',
          amount: 300,
          time: new Date('20 Mar 2023')
        },
        {
          id: 9,
          title: 'Movimiento 10',
          description: 'Lorem ipsum dolor sit amet',
          amount: 500,
          time: new Date('19 Mar 2023')
        }
      ]
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
    }
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
    },
    remove(id) {
      const index = this.movements.findIndex(m => m.id === id);
      this.movements.splice(index, 1);
    }
  }
}
</script>