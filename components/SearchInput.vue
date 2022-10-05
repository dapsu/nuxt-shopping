<template>
  <div>
    <input 
    type="text" 
    :value="value" 
    @input="$emit('input', $event.target.value)"
    @keyup.enter.exact="$emit('search')">
    <button type="button" @click="$emit('search')">search</button>
  </div>
</template>

<script>
export default {
  props: {
    value: {  // v-model 사용 시 props는 value로!
      type: String,
      default: "",
    },
    // searchKeyword: {
    //   type: String,
    //   default: () => "",
    // },
  },
}
</script>

<style>

</style>