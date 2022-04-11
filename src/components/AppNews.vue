<template>
  <div
      class="card"
  >
    <h3>{{ title }}</h3>
    <div style="display: flex; justify-content: center">
      <button class="btn" @click="openNews">{{ isNewOpen ? 'Закрыть' : 'Открыть' }}</button>
      <button class="btn danger" v-if="wasRead" @click="$emit('unmark', id)">Отметить непрочитанной</button>
    </div>

    <div v-if="isNewOpen">
      <p>{{ body }}</p>
      <hr>
      <button v-if="!wasRead" class="btn primary" @click="$emit('on-read', id)">Прочесть новость</button>
    </div>
  </div>
</template>

<script>
export default {
  // props: ['title'],
  emits: {
    'open-news': null,
    'on-read'(id) {
      if (id) {
        return true
      }
      console.warn('Нет параметра id у on-read')
      return false
    },
    unmark(id) {
      if (id) {
        return true
      }
      console.warn('unmark что то не то')
      return false
    }
  },
  props: {
    title: String,
    id: Number,
    body: String,
    isOpen: Boolean,
    wasRead: Boolean
  },
  data() {
    return {
      isNewOpen: this.isOpen
    }
  },
  methods: {
    openNews() {
      this.isNewOpen = !this.isNewOpen
      this.isNewOpen ? this.$emit('open-news', this.title) : ''
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

.danger {
  background: rosybrown;
}

.primary {
  background: lavender;
  color: black;
}
</style>