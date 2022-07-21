<template>
  <div>
    <slot :user="user">{{ user.name }}</slot>
  </div>
</template>

<script>
export default {
  name: 'SlotTest',
  components: {
  },
  data() {
    return {
      user: {
        name: 'zww',
        age: '18'
      }
    }
  },
  computed: {
  },
  created() {
  },
  mounted() {
  },
  methods: {}
}
</script>

<style lang='scss'>
</style>
