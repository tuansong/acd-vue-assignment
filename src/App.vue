<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col lg="8">
          <h1>TABS AND PILLS</h1>
          <h2 class="mt-4">HORIZOTAL TABS - STYLE 1</h2>
          
          <b-tabs>
            <b-tab v-for="data of tabData" 
                  v-bind:key="data.id"
                  v-if="data.usable"
                  active>
              <template slot="title">
                <span v-if="data.id == 1"><i class="fas fa-home"></i></span>
                <span v-else-if="data.id == 2"><i class="fas fa-user-alt"></i></span>
                <span v-else-if="data.id == 3"><i class="fas fa-envelope"></i></span>
                {{data.title}}
              </template>
              <h3>{{data.title}}</h3>
              <b-row>
                <b-col md="6">
                  <p>{{data.description}}</p>
                </b-col>
                <b-col md="6">
                  <ul v-for="child of data.children" v-bind:key="child.id">
                    <li><i class="fas fa-check"></i> {{child.text}}</li>
                  </ul>
                </b-col>
              </b-row>
              <button class="btn btn-md btn-primary">Read more</button>
            </b-tab>
          </b-tabs>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import data from './data.json';
export default {
  name: 'app',
  data () {
    return {
      tabData: data.items,
      icons: ['fas fa-home', 'fas fa-user-alt', 'fas fa-envelope']
    }
  }
}
</script>

<style>
#app {
  font-family:'Times New Roman', Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color:black;
  margin-top: 60px;
}

h1 {
  margin-bottom: 2em;
  font-size: 200%;
}

h1,h2 {
  font-weight: bold;
  font-family: "Raleway", sans-serif;
}

h2 {
  font-size: 180%;
}

.nav-item {
  background-color: transparent;
  border: none;
}

.nav-link {
  color: black;
  text-decoration: underline;
}

.nav-link.focus {
  color: black;
}

.nav-link.active {
  background-color: #333333!important;
  color: white!important;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  text-decoration: none;
}

ul li {
  list-style: none;
}
</style>
