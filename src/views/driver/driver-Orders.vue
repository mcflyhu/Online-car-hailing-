import VueAMap from '@vuemap/vue-amap'
<template>
  <div class="A-Map">
    <get-orders />
    <Map_index />
  </div>
</template>

<script>
import Map_index from '../amap/index.vue'
import getOrders from './order-items.vue'
export default {
    name: 'DriverOrder',
    components: { Map_index, getOrders },
    data() {
        return {}
    },
    methods: {

    }
}
</script>
<style lang="scss">
@import "./index.scss"
</style>
