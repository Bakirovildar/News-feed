<template>
  <h1>Актуальные новости {{ now }}</h1>
  <span>Открыто {{ openRate }} раз | Прочитано {{ openRead }}</span>
  <AppNews
      v-for="item in news"
      :key="item.id"
      :title="item.title"
      :id="item.id"
      :body="item.body"
      :is-open="item.isOpen"
      :wasRead="item.wasRead"
      @open-news="countRate"
      @on-read="onRead"
      @unmark="unReadNews"
  />
</template>

<script>
import AppNews from './AppNews'

export default {
  data() {
    return {
      now: new Date().toLocaleDateString(),
      news: [
        {
          id: 1,
          title: 'В Уфе солнечная погода',
          isOpen: false,
          wasRead: false,
          body: 'lorem ipsum Lorem ipsum dolor sit amet, consectetur adipisicing elit. Delectus eaque earum, itaque libero odio quaerat. '
        },
        {
          id: 2,
          title: 'Vue 3 работате отлично',
          isOpen: false,
          wasRead: false,
          body: 'lorem ipsum Lorem ipsum dolor sit amet, consectetur adipisicing. '
        },
      ],
      onShowText: false,
      openRate: 0,
      openRead: 0
    }
  },
  components: {
    AppNews
  },
  methods: {
    countRate() {
      this.openRate++
    },
    onRead(id) {
      this.news.map(i => i.id === id ? i.wasRead = true : '')
      this.openRead++
    },
    unReadNews(id) {
      const news = this.news.find(i => i.id === id)
      news.wasRead = false
      this.openRead--
    }
  }
}

</script>

<style>
</style>