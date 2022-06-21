<template>
  <p class="ref">ref demo: {{name}}, {{age}}</p>

</template>
<script>
import { ref, reactive } from 'vue'
export default {
  setup() {
    let name = ref('vue')
    let age = ref(18)
    // const state = reactive({
    //   name,
    //   age
    // })
    // const stateRef = ref(state)

    setTimeout(() => {
      console.log('setTimeout')
      name.value = 'vue3'
    }, 500);
    return {
      // stateRef,
      name,
      age
    }
  }
}
</script>