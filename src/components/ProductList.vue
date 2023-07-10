<template>
    
  <div>
    <img :src="product.img" alt="" style="width:300px; height: 180px;">
        <h4 @click="$emit('open');">{{ product.name }}</h4>
        <p>{{ product.price }}</p>
        <button @click="$emit('add')">+</button>
        <button v-if="product.count <= 0" type="button">-</button>
        <button v-else-if="product.count > 0" @click="$emit('remove')">-</button>
        <p>count : <span>{{ product.count }}</span></p>
        <p>total price : <span>{{ product.price * product.count }}</span></p>
  </div>
</template>

<script>
export default {
    name: 'ProductList',
    props: {
        product: Object,
        proNum: Number,
    }
}
</script>

<style>

</style>