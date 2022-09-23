<template>
  <input :value="modelValue" @input="updateInput" class="v-input" type="text">
</template>

<script>
export default {
  name: "v-input",
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event){
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped lang="scss">
.v-input{
  max-width: 100%;
  width: 315px;
  box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  -webkit-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  -moz-box-shadow: 0 5px 10px 2px rgba(34, 60, 80, 0.05);
  padding: 0 15px;
  margin-top: 15px;
  background-color: #ffffff;
  border-radius: 0 5px 5px 0;

  &:focus{
    outline: 1px solid #75aae9;
  }
}

</style>