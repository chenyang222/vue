<template>
    <div>
        <p>{{ testData }}</p>
        <button @click='sendMsgToParent'>子组件传给父组件</button>
        <p>从child2传过来的数据 {{ fromChild2 }}</p>
    </div>
</template>

<script>
import bus from '../../assets/eventBus'

export default {
  data () {
    return {
      fromChild2: ''
    }
  },
  props: ['testData'],
  created () {
    console.log(this)
  },
  mounted () {
    var _this = this
    bus.$on('userDefinedEvent', function (msg) {
      _this.fromChild2 = msg
    })
  },
  methods: {
    sendMsgToParent: function () {
      this.$emit('listenToChildEvent', 'this message from child!')
    }
  }
}
</script>

<style scoped>

</style>
