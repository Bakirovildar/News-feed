<template>
  <div
      class="card"
  >
    <h3>{{ title }}</h3>
    <button class="btn" @click="openNews">{{isNewOpen ? 'Закрыть' : 'Открыть'}}</button>
    <p v-if="isNewOpen">{{ body }}</p>
  </div>
</template>

<script>
export default {
  // props: ['title'],
  props: {
    title: String,
    id: Number,
    body: String,
    isOpen: Boolean
  },
  data() {
    return {
      isNewOpen: this.isOpen
    }
  },
  methods: {
    openNews() {
      this.isNewOpen = !this.isNewOpen
      this.isNewOpen ? this.$emit('open-news') : ''
    }
  }
}
</script>

<style>

.card {
  border: 1px solid black;
  border-radius: 8px;
  margin: 10px;
  background: darkseagreen;
}

.btn {
  border: none;
  width: 140px;
  height: 40px;
  margin: 5px;
  border-radius: 20px;
  background: #2c3e50;
  color: white;
  cursor: pointer;
}
</style>