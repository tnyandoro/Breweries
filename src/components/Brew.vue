<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Breweries List</h1> 
      </div>
      <!-- /.col-12 -->
    </div>
    <!-- /.row -->
    <div class="row">
      <div class="col-6 brew-list">
        <div class="card">
          <b-card header="Card with list group">
            <ul class="list-group list-group-flush">
              <li 
                v-for="(brew, index) in brews" v-bind:key="index"
              class="list-group-item"
              >{{index}}, {{brew.name}}, {{brew.state}}</li>
              
            </ul>
          </b-card>
        </div>
      </div>
      <div class="col-6">
        <h2 class="text-center">right</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'


export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Brew',
  data() {
    return {
      brews: [{brew: 'name'}, {brew:'state'}]
    }
  },

  mounted: function() {
    //https://api.openbrewerydb.org/breweries
    axios.get ('https://api.openbrewerydb.org/breweries')
      .then((r) => {
       this.brews = (r.data);
      })
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
   .brew-list {
    overflow-y: scroll;
    height:  95vh;
    li {
      &:hover {
        background-color: #313b45;
      }
    }
   }
</style>
