<template>
  <div class="launch-wrapper">
    <div class="launch-info">
      <img class="rocket-image" src="../assets/falcon9.png">
      <div class="rocket-name info-item">
        <b>Rocket -</b> {{ launch.rocket.rocket_name }}
      </div>
      <div class="launch-date info-item">
        <b>Date -</b> {{ launch.launch_date_local }}
      </div>
      <div class="launch-site info-item">
        <b>Launch Site -</b> {{ launch.launch_site.site_name_long }}
      </div>
    </div>
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

<style scoped>
  .launch-wrapper {
    display: flex;
    flex-direction: column;
    width: 300px;
    height: 280px;
    background-color: white;
    border-radius: 20px;
    color: black;
    padding: 0 10px 0 10px;
  }

  .launch-info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    top: -70px;
  }

  .rocket-image {
    height: 140px;
    width: 140px;
    border-radius: 100%;
    border: 3px solid white;
    box-shadow: 0 10px 25px 0 rgba(0,0,0,.3);
    margin-bottom: 30px;
  }

  .info-item {
    margin-bottom: 15px;
  }

  .rocket-name {
  }

  .launch-date {

  }

  .launch-site {
    margin-bottom: 0;
  }
</style>
