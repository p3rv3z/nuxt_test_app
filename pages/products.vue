<template>
<div>
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto">
      <div class="flex flex-col text-center w-full mb-20">
          <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Products</h1>
        </div>
      <div class="flex flex-wrap -m-4">
        <div v-for="product in products" :key="product.id" class="lg:w-1/4 md:w-1/2 p-4 w-full">
          <a class="block relative h-48 rounded overflow-hidden">
            <img alt="ecommerce" class="object-cover object-center w-full h-full block" src="https://dummyimage.com/420x260">
          </a>
          <div class="mt-4">
            <h3 class="text-gray-500 text-xs tracking-widest title-font mb-1">Seller: {{product.user.name}}</h3>
            <h2 class="text-gray-900 title-font text-lg font-medium">{{product.title}}</h2>
            <p class="mt-1">{{product.price}}TK</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</div>

</template>

<script>
export default {

  async asyncData({$axios, redirect}) {
    try {
      const products = await $axios.$get('products')
      return { products }
    } catch (error) {
      redirect('/error')
    }
  },
}
</script>
