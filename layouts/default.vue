<template>
  <div>
    <header>
      <h1>{{ $route.name }} 페이지</h1>
      <Nuxt-link to="/">홈페이지</Nuxt-link>
      <Nuxt-link to="/main">메인 페이지</Nuxt-link>
      <Nuxt-link to="/product">상품 페이지</Nuxt-link>
    </header>
    <Nuxt />
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>