<template>
    <div>
        <button @click='sendChildMsg'>子组件2传给传给子组件1</button>
    </div>
</template>

<script>

import bus from '../../assets/eventBus'

export default {
  data () {
    return {}
  },
  created () {
    console.log(this)
  },
  methods: {
    sendMsgToParent: function () {
      this.$emit('listenToChildEvent', 'this message from child!')
    },
    sendChildMsg: function () {
      bus.$emit('userDefinedEvent', 'this message is from child2!')
    }
  }
}
</script>

<style scoped>

</style>
