<template>
  <div class="main-wrapper">
    SpaceX Launches
    <div class="missions" v-for="launch in launches">
      <mission-card :launch="launch"></mission-card>
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
  .main-wrapper {
    /* color: white; */
  }

</style>
