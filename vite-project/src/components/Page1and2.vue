<template>
  <div style="display: flex; justify-content: center">
    <a href="#" @click="toggleUserList(1)">
      <p>1</p>
    </a>
    <a href="#" @click="toggleUserList(2)">
      <p style="padding-left: 5px">2</p>
    </a>
  </div>
</template>

<script lang="ts">
export default {
  name: "Page1and2",
  methods: {
    toggleUserList(selected: number) {
      this.$emit('select-number', selected);
    },
  },
};
</script>