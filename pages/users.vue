<template>
<div>
  <div v-if="$fetchState.pending" class="mt-64 text-xl font-medium text-center">
    <p>Loading...</p>
  </div>
  <div v-else-if="$fetchState.error" class="mt-64 text-xl font-medium text-center text-red-700">
    <p>An error occurred :(</p>
  </div>
  <section v-else class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex flex-col text-center w-full mb-20">
      <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Users</h1>
    </div>
    <div class="flex flex-wrap -m-2">
      <div v-for="user in users" :key="user.id" class="p-2 lg:w-1/3 md:w-1/2 w-full">
        <div class="h-full flex items-center border-gray-200 border p-4 rounded-lg">
          <img alt="team" class="w-16 h-16 bg-gray-100 object-cover object-center flex-shrink-0 rounded-full mr-4" src="https://dummyimage.com/80x80">
          <div class="flex-grow">
            <h2 class="text-gray-900 title-font font-medium">{{user.name}}</h2>
            <p class="text-gray-500">{{user.email}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
</div>

</template>

<script>
export default {

  data: () => ({
    users: []
  }),

  async fetch() {
    this.users = await this.$axios.$get('users')
  },
}
</script>
