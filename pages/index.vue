<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    const { data } = await axios.get(
      // your-service-id部分は自分のサービスidに置き換えてください
      'https://d-fuchi.microcms.io/api/v1/blog',
      {
        // your-api-key部分は自分のapi-keyに置き換えてください
        headers: { 'X-MICROCMS-API-KEY': '4a0d350f983c4749a61f6bbdb94ff4b48ce1' }
      }
    )
    return data
  }
}
</script>