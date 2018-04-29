<template>
  <div class="launch-wrapper">
    <div class="launch-info">
      <img class="rocket-image" src="../assets/falcon9.png">
      <div class="rocket-name info-item">
        <b>Rocket -</b> {{ launch.rocket.rocket_name }}
      </div>
      <div class="launch-date info-item">
        <b>Date -</b> {{ launchDate }}
      </div>
      <div class="launch-time info-item">
        <b>Time -</b> {{ launchTime }}
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
      launchDate: null,
      launchTime: null,
    }
  },

  mounted() {
    // Create a new JavaScript Date object based on the timestamp
    // multiplied by 1000 so that the argument is in milliseconds, not seconds.
    let a = new Date(this.launch.launch_date_unix * 1000);
    let months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'];
    let year = a.getFullYear();
    let month = months[a.getMonth()];
    let date = a.getDate();

    let fullDate = date + ' ' + month + ' ' + year;
    this.launchDate = fullDate;

    let time = this.launch.launch_date_utc;
    let utcTime = time.split('T')[1];
    this.launchTime = utcTime.substring(0, utcTime.length - 1);


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
    box-shadow: 0 1px 15px 1px rgba(39,39,39,.1);
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
    margin-bottom: 20px;
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
