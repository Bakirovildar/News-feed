<template>
  <h1>Актуальные новости {{now}}</h1>
  <span>Открыто {{openRate}} раз</span>
  <AppNews
      v-for="item in news"
      :key="item.id"
      :title="item.title"
      :id="item.id"
      :body="item.body"
      :is-open="item.isOpen"
      @open-news="openRate++"
  />
</template>

<script>
import AppNews from './AppNews'
export default {
  data() {
    return {
      now: new Date().toLocaleDateString(),
      news: [
        {id: 1, title: 'В Уфе солнечная погода', isOpen: false, body: 'lorem ipsum Lorem ipsum dolor sit amet, consectetur adipisicing elit. Delectus eaque earum, itaque libero odio quaerat. '},
        {id: 2, title: 'Vue 3 работате отлично', isOpen: false, body: 'lorem ipsum Lorem ipsum dolor sit amet, consectetur adipisicing. '},
      ],
      onShowText: false,
      openRate: 0
    }
  },
  components: {
    AppNews
  }
}

</script>

<style>
</style>