<template>
    <div class="app">
        <ImageAttached />
        <Preloader />
    </div>
</template>

<script>
import ImageAttached from './components/ImageAttached.vue';
import Preloader from './components/Preloader.vue';

export default {
  components: {
    ImageAttached,
    Preloader
  }
}
</script>

<style scoped>

</style>
