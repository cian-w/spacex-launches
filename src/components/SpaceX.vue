<template>
  <div class="main">
    <div class="header">SpaceX Launches</div>

    <div class="launch-wrapper">
      <div class="launch" v-for="launch in launches">
        <mission-card :launch="launch"></mission-card>
      </div>
    </div>
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

  .header {
    margin-top: 20px;
    font-size: 30px;
  }

  .launch-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 60%;
    color: white;
    margin-left: auto;
    margin-right: auto;
  }

  .launch {
    margin-top: 100px;
  }

</style>
