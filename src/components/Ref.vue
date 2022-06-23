<template>
  <p class="ref">ref demo: {{ state.name }}, {{ ageRef }}</p>

</template>
<script>
import { ref, reactive, watch, watchEffect } from 'vue'
export default {
  setup() {
    let nameRef = ref('vue')
    let ageRef = ref(18)

    const state = reactive({
      name: nameRef
    })

    watch(
      () => state.name,
      (oldVal, newVal) => {
        console.log("watch>>", oldVal, newVal)
      },
      {
        // immediate: true,
        // deep: true,
      }
    )

    watchEffect(
      () => {
        console.log('初始化一定会执行一次')
        console.log('state>>', state.name)
      }
    )

    setTimeout(() => {
      console.log('setTimeout')
      ageRef.value = 21
      state.name = 'vin'
    }, 500);

    return {
      state,
      ageRef
    }
  }
}
</script>