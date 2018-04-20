<template>
  <div class='hello'>
    <div>
      {{ msg }}
    </div>
    <Child-Components :testData='testData' v-on:listenToChildEvent='showMsgFromChild'></Child-Components>
    <Child-Components2></Child-Components2>
  </div>
</template>

<script>

import ChildComponents from './child/child'
import ChildComponents2 from './child2/child2'

export default {
  name: 'hello',
  data () {
    return {
      msg: '父级组件',
      testData: '123456'
    }
  },
  methods: {
    showMsgFromChild: function (data) {
      console.log(data)
      this.testData = data
    }
  },
  components: {
    ChildComponents,
    ChildComponents2
  }
}
</script>

<style scoped>

</style>
