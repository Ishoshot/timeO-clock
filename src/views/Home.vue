<template>
  <div class="home">
    <Clock />
  </div>
</template>

<script>
// @ is an alias to /src
import Clock from '@/components/Clock.vue'

export default {
  name: 'home',
  components: {
    Clock
  }
}
</script>
