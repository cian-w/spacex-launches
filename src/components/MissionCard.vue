<template>
  <div class="mission-wrapper">
    <p>{{launch.launch_year}}</p>
    <p>{{launch.launch_date_local}}</p>
  </div>
</template>

<script>
export default {
  name: 'MissionCard',

  props: ['launch'],

  data () {
    return {

    }
  }

}
</script>

<style>

</style>
