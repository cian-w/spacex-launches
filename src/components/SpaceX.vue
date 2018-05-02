<template>
  <div class="main">
    <div class="header">
      <img class="spacex-logo" src="../assets/spacexlogo.png">
    </div>

    <div class="launch-wrapper">
      <div class="launch" v-for="launch in launches">
        <mission-card :launch="launch"></mission-card>
      </div>
    </div>
    <a class="data-source" href="https://api.spacexdata.com/v2/launches/upcoming">Data Source</a>
  </div>
</template>

<script>
import axios from 'axios'
import MissionCard from '@/Components/MissionCard'

export default {
  name: 'SpaceX',

  components: { MissionCard },

  data () {
    return {
      launches: [],
      name: 'cian'
    }
  },

  created() {
    axios.get(`https://api.spacexdata.com/v2/launches/upcoming`, {})
      .then(response => {
        this.launches = response.data;
      })
      .catch(e => {
        console.log('Error getting SpaceX Launches :(', e);
      }
    );
  }

}
</script>

<style scoped>
  .main {
    display: flex;
    flex-direction: column;
  }

  .spacex-logo {
    height: 100px;
    width: 300px;
  }

  .header {
    margin-top: 0px;
    font-size: 30px;
  }

  .launch-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    width: 60%;
    max-width: 1000px;
    color: white;
    margin-left: auto;
    margin-right: auto;
  }

  .launch {
    margin-top: 100px;
  }

  .data-source {
    text-decoration: none;
    color: black;
    margin: 20px;
  }

  @media (max-width: 1067px) {
    .launch-wrapper {
      display: flex;
      flex-direction: column;
    }
  }


</style>
