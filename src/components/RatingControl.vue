<template>
  <ul>
    <li :class="{active: actioveOptions === 'poor'}">
      <button 
      type="button" 
      @click="activate('poor')"
      >Poor</button>
    </li>
    <li :class="{active: actioveOptions === 'average'}">
      <button 
      type="button" 
      @click="activate('average')"
      >Average</button>
    </li>
    <li :class="{active: actioveOptions === 'great'}">
      <button 
      type="button" 
      @click="activate('great')"
      >Great</button>
    </li>
    <star></star>
  </ul>
</template>

<script>
  export default {
    props:['modelValue'],
    emits: ['update:modelValue'],
    data() {
      return {
        actioveOptions: this.modelValue,
      }
    },
    computed: {
      actioveOptions() {
        return this.modelValue;
      }
    },
    methods: {
      activate(option) {
        this.actioveOptions = option;
        this.$emit('update:modelValue', option);
      }
    }
  }
</script>

<style scoped>
.active {
  border-color: red;
  background-color: aqua;
}

.active button {
  color: red;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>