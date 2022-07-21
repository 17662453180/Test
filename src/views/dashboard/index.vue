<template>
  <div class="dashboard-container">
    <div class="dashboard-text">name: {{ name }}</div>
    <div class="dashboard-text">name: {{ name }}</div>
    <div class="dashboard-text">name: {{ name }}</div>
    <div class="dashboard-text">name: {{ name }}</div>
    <p v-for="item in items" :key="item.id">
      {{ item.message }}
    </p>
    <el-button @click="test">this.$set测试</el-button>
    <SlotTest>
      <template slot-scope="slotProps">{{ slotProps.user.age }}</template>
    </SlotTest>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import SlotTest from '@/components/test/slot-test'

export default {
  name: 'Dashboard',
  components: {
    SlotTest
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  data() {
    return {
      obj: {
        name: '123'
      },
      items: [
        { message: 'one', id: '1' },
        { message: 'two', id: '2' },
        { message: 'three', id: '3' }
      ]
    }
  },
  created() {
    window.myData = this
    const obj1 = {
      name: 'jack',
      sex: undefined,
      age: 25,
      hobby: {
        ball: 'tennis'
      }
    }
    const obj2 = Object.assign({}, obj1)
    // const obj2 = JSON.parse(JSON.stringify(obj1))

    // obj2.hobby.ball = 'basketball'
    // obj2.name = 'zww'
    const arr1 = ['1', '2', ['a', 'b']]
    const arr2 = [...arr1]
    arr2[2][0] = 'zww'
    // console.log('arr1', arr1) // basketball
    // console.log('arr2', arr2) // basketball
    console.log('obj1', obj1) // basketball
    // console.log('obj2', obj2) // basketball
  },
  methods: {
    test() {
      this.items[0] = { message: 'first', id: '4' }
      this.$set(this.items, 0, { message: 'first', id: '4' })
      console.log('shuchu', this.items)
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
