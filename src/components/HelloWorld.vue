  <template>
  <div class="page-container">
    <md-app md-waterfall md-mode="overlap">
      <md-app-toolbar class="md-primary md-large">
        <div class="md-toolbar-row">
          <md-button class="md-icon-button" @click="menuVisible = !menuVisible">
            <md-icon>menu</md-icon>
          </md-button>

          <span class="md-title"><img width="50%" src="https://developers.amadeus.com/PAS-EAS/api/v1/cms-gateway/sites/default/files/2019-09/logo-portal.png"></span>
        </div>
      </md-app-toolbar>

      <md-app-drawer :md-active.sync="menuVisible">
        <md-toolbar class="md-transparent" md-elevation="0">
          Navigation
        </md-toolbar>

        <md-list>
          <md-list-item>
            <md-icon>move_to_inbox</md-icon>
            <span class="md-list-item-text">Inbox</span>
          </md-list-item>

          <md-list-item>
            <md-icon>send</md-icon>
            <span class="md-list-item-text">Sent Mail</span>
          </md-list-item>

          <md-list-item>
            <md-icon>delete</md-icon>
            <span class="md-list-item-text">Trash</span>
          </md-list-item>

          <md-list-item>
            <md-icon>error</md-icon>
            <span class="md-list-item-text">Spam</span>
          </md-list-item>
        </md-list>
      </md-app-drawer>

      <md-app-content>
        
<!-- https://codepen.io/sarahspr/pen/jQVeZr -->
    <!-- form -->
    <main class ="content">
    <form class="form">
    <div class ="title">
      <h1>Book a Flight</h1>
        <p>Select locations and dates to get started.</p>
    </div>
    <div class="progress">
      <p>Step 1 of 3</p>
    <div class="progress-bar">
      <div class="bar-pink">
        <p>33%</p>
      </div>
     </div>
    </div>
    <div class ="categories">
      <button class="flights button">Flights</button>
      <button class="Hotels button">Hotels</button>
      <button class ="Packages button">Packages</button>
    </div>
   <div class="row1">
    <div class="locations from-location1">
     <md-autocomplete @input="autocompleteCity" v-model="selectedCountry" :md-options="countries">
      <label>Country</label>
    </md-autocomplete>
    </div>
    <div class="locations to-location1">
      <md-autocomplete @input="autocompleteCity" v-model="selectedCountry" :md-options="countries">
      <label>Country</label>
    </md-autocomplete>
    </div>
  </div>
    <div class="row2">
      <div class="dates depart">
        <label class="depart-date" for="depart">Depart:</label>
        <input class="departure-date" type="date"/>
      </div>
      <div class="dates return">
        <label class="returning-date" for="return">Return:</label>
        <input class="return-date" type="date"/>    
      </div>
    </div>
    <div class="next-button">
    <button class="next" value="submit">Let's Fly!</button>
      </div>
    </form>
  </main>
       <div >{{token}}
      <div class="row">
    <div v-for="item in info2" :key="item.links.flightOffers" class="col s4 autoflow">
      <div class="card blue-grey darken-1">
        <div class="card-content white-text">
          <span class="card-title"> {{item.destination}}</span>
          <p>{{item.destination}}--{{item.price.total}}</p>
        </div>
        <div class="card-action">
          <a :href="item.links.flightDates">check offer</a>
          <a :href="item.links.flightOffers">This is a link</a>
        </div>
      </div>
    </div>
  </div>


   </div>
      </md-app-content>
    </md-app>
  </div>
</template>


<style  scoped>
/*  .md-app {
    max-height: 400px;
    border: 1px solid rgba(#000, .12);
  }

  
  .md-drawer {
    width: 230px;
    max-width: calc(100vw - 125px);
  }*/

  .content {
  max-width: 65%;
  max-height: 100%;
  margin: 75px auto;
  border-radius: 6px;
  background-color: #424242
}

.form {
  text-align: center;
}

.title {
  text-align: center;
  padding-top: 10px;
}

.progress {
  width: 80%;
  display: inline-block;
  text-align: center;
}

.progress-bar {
  background-color: #FEAFEB;
  margin-bottom: 20px;
  border-radius: 16px;
}

.bar-pink {
  height: 26px;
  width: 33%;
  background-color: #FF33CE;
  color: white;
  border-radius: 16px;
}

.categories {
  width: 100%;
  display: inline-block;
}

.button {
  background-color: #F3F3F3;
  width: 33.3%;
  border: none;
  color: #7E7E7E;
  font-size: 16px;
  font-weight: bold;
  padding: 15px;
}

button:hover {
  background-color: #FF33CE;
  color: white;
}

.Hotels {
  margin-left: -4px;
  margin-right: -4px;
}

.row1 {
  width: 100%;
  margin-top: 30px;
  font-size: 18px;
}

.locations {
  display: inline-block;
}

.from-location2 {
  color: #7E7E7E;
}

.from {
  -webkit-appearance: none;
  background-color: #F3F3F3;
  padding: 8px 20px;
  border: none;
}

.from-location1 {
  width: 45%;
}

.to-location1 {
  width: 45%;
}

.to-location2 {
  color: #7E7E7E;
}

.to {
  -webkit-appearance: none;
  background-color: #F3F3F3;
  padding: 8px 20px;
  border: none;
}

.row2 {
  width: 100%;
  margin-top: 30px;
  font-size: 18px;
}

.dates {
  display: inline-block;
  border: none;
}

.depart {
  width: 45%;
  color: #7E7E7E;
}

.departure-date {
  border: none;
  padding: 8px 8px;
  background-color: #F3F3F3;
}

.return {
  width: 45%;
  color: #7E7E7E;
}

.return-date {
  border: none;
  padding: 8px 8px;
  background-color: #F3F3F3;
}

.next-button {
  padding-top: 10px;
  padding-bottom: 10px;  
}

.next {
  display: block;
  margin: 20px auto 20px;
  padding: 10px 20px;
  font-size: 14px;
  background-color: #FF33CE;
  color: white;
  border: none;
  border-radius: 16px; 
}

.next:hover {
  background-color: #D52CAC;
}
</style>

<script>
export default {
  name: 'Overlap',
  data: () => ({
    menuVisible: false,
    selectedCountry: null,
    countries: [
        'Algeria',
        'Argentina',
        'Brazil',
        'Canada',
        'Italy',
        'Japan',
        'United Kingdom',
        'United States'
      ],
      localhost: "https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT,CITY&keyword=",
      info:{},
  info2:{},
  token:"",
  localhost3: "http://localhost:3000/token",
  localhost2: "http://localhost:3000/flight",
  }),
created() {
var vm=this;
fetch(vm.localhost3).then(function(response) {
// Examine the text in the response
response.json().then((response) => {
  window. console.log(response)
  vm.token=response
})
}
);


//get flight inspirations search

const uriAuth ="http://localhost:3000/flight" 


// //get grant
// let headers= {
//       // 'Content-Type': 'application/json'   
//       'Content-Type': 'application/x-www-form-urlencoded',
//      };

// let body = {
//    "grant_type": "client_credentials",
//    "client_id": "qztkbf5XWjNSGkXRF9bfAwNg6bELWvVD",
//   "client_secret": "w9mJ7ZJzlEGNffut",
  
// }

// let token="";

fetch(uriAuth)
  .then((res) => {
     return res.json()
})
.then((json) => {
  window.console.log(json);

  this.info2=json.data;

// window.console.log(token);

  
  // Do something with the returned data.
});
  
},  

methods: {

        }
}
</script>
  
