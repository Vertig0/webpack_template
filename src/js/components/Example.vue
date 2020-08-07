<template>
  <section>
    <div class="container">
      <img src="/assets/img/logo.jpg" :alt="message" />
      <p>{{ message }}</p>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      message: 'Пример Vue component'
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  text-align: center;
}
img {
  max-width: 200px;
}
</style>
