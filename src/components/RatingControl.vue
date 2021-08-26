<template>
  <ul>
    <!-- we add the type as button so it doesnt submit the form on clicking , because the default type for a button is submit  -->
    <li>
      <button
        :class="{ active: activeOption === 'poor' }"
        type="button"
        @click="activate('poor')"
      >
        Poor
      </button>
    </li>
    <li>
      <button
        :class="{ active: activeOption === 'average' }"
        type="button"
        @click="activate('average')"
      >
        Average
      </button>
    </li>
    <li>
      <button
        :class="{ active: activeOption === 'great' }"
        type="button"
        @click="activate('great')"
      >
        Great
      </button>
    </li>
  </ul>
</template>
<script>
export default {
  props: ["modelValue"],
  emits: ["update:modelValue"],
  //   data() {
  //     return {
  //       activeOption: this.modelValue,
  //     };
  //   },
  // we have used the computed property here because
  // data is not reactive when props gets updated
  computed: {
    activeOption() {
      return this.modelValue;
    },
  },
  methods: {
    activate(option) {
      this.activeOption = option;
      this.$emit("update:modelValue", option);
      //   console.log(this.activeOption);
    },
  },
};
</script>
<style scoped>
button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
.active {
  color: blue;
}

.active button {
  color: violet;
}
ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}
li {
  margin: 0 1rem;
  border: 1px solid £ccc;
  display: flex;
  padding: 1rem;
  justify-content: center;
  align-items: center;
}
</style>
