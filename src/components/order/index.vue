<template>
  <div class="Orders">
    <div v-if="show_details">
      <ul class="help-set-safe">
        <li><a href="javascrit:void();" class="cmb" @click="comeback">
          <img src="./components/components/返回.svg">
        </a></li>
        <li>
          <getOrderItems />
        </li>
      </ul>
    </div>
    <div v-if="show_bar" class="bar">
      <ul class="help-set-safe">
        <li><a href="javascrit:void();" @click="selfLocation">
          <img src="./components/定位-定位.svg">
        </a></li>
        <li><a href="javascrit:void();">
          <img src="./components/取消.svg" @click="getDetails">
        </a></li>
        <li><a href="javascrit:void();">
          <img src="./components/安全.svg">
        </a></li>
      </ul>
      <ul class="btn-class">
        <li>
          <a href="javascrit:void();" class="order-btn" @click="jumpto">{{ call }}</a>
          <a href="javascrit:void();" class="order-btn" @click="jumptoA">{{ order }}</a>
        </li>
      </ul>
      <ul class="locate">
        <li><a href="javascrit:void();">
          <img src="./components/帮助.svg">
        </a></li>
        <li><a href="javascrit:void();">
          <img src="./components/设置.svg">
        </a></li>
        <li><a href="javascrit:void();" @click="jump">
          <img src="./components/头像.svg">
        </a></li>
      </ul>
    </div>
  </div>
</template>

<script>
import getOrderItems from './components/order-item.vue'
export default {
  name: 'Orders',
  components: {
    getOrderItems
  },
  props: {
    order: {
      type: String,
      default: '点击约车'
    },
    call: {
      type: String,
      default: '点击叫车'
    },
    identity: {
      type: String,
      default: 'true'
    },
    show_details: {
      type: Boolean,
      default: false
    },
    show_bar: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    jump() {
      this.$router.replace({
        name: 'Dashboard'
      })
    },
    jumpto() {
      if (this.identity === 'true') {
        this.$router.replace({
          name: 'getOrder'
        })
      } else {
        this.$router.replace({
          name: 'driver-order'
        })
      }
    },
    jumptoA() {
      if (this.identity === 'true') {
        console.log(1111)
        this.$router.replace({
          name: 'getAppointments'
        })
      } else {
        console.log(22222)
        this.$router.replace({
          name: 'driver-appointments'
        })
      }
    },
    selfLocation() {
      this.$store.commit('location/SELF_LOCATION')
    },
    getDetails() {
      this.show_bar = false
      this.show_details = true
    },
    comeback() {
      this.show_bar = true
      this.show_details = false
    }
  }
}

</script>
<style lang="scss">
@import "./index.scss"
</style>
