<script>
export default {
  data() {
    return {
      products: [
        {
          id: "1",
          name: "airpods"
        },
        {
          id: "2",
          name: "kindle"
        },
        {
          id: "3",
          name: "keyboard"
        }
      ]
    }
  }
}
</script>
<template>
  <div v-for='product in products':key='product.id'>
    <h3>{{ product.id }} : {{ product.name }}</h3>
  </div>
</template>