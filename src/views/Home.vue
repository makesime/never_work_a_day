<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <moment-list/>
  </div>
</template>

<script>
// @ is an alias to /src
import MomentList from '../components/MomentList.vue'

export default {
  name: 'Home',
  components: {
    MomentList
  }
}
</script>