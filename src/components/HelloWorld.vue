<template>
  <div class="hello">
<div class="container">
<div class="">
   <!-- <div v-for="item in info" :key="item.departureDate">
     {{item.origin}}--{{item.destination}}--{{item.price.total}}
   </div> -->
   <div >
      <div class="row">
    <div v-for="item in info2" :key="item.departureDate" class="col s4 autoflow">
      <div class="card blue-grey darken-1">
        <div class="card-content white-text">
          <span class="card-title">{{item.destination}}</span>
          <p>{{item.price.total}}--{{item.departureDate}}--{{item.returnDate}}</p>
        </div>
        <div class="card-action">
          <a :href="item.links.flightOffers">check offer</a>
          <a href="#">This is a link</a>
        </div>
      </div>
    </div>
  </div>


   </div>
   </div>
 </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },data: () => ({
  info:{},
  info2:{},
  localhost: "http://localhost:3000",
  localhost2: "http://localhost:3000/flight",
  //localhost2: "http://peslmwefulb01.es.corp.leroymerlin.com:8080/Ctrl_Gestion/",
  //dev : "http://10.24.67.66:3000",
 // Download : "Descargar",
 //slash : "/"
}),
mounted () {
},

filters : {
  transformPath: function (value){
    var newString=value.replace("/home4/board_ftp/","");
    newString.toString()
    window.console.log(newString)
    return newString

  }
},created() {
var vm=this;
fetch(vm.localhost).then(function(response) {
  if (response.status !== 200) {
    window.console.log('Looks like there was a problem. Status Code: ' +
      response.status);
    return;
  }
// Examine the text in the response
response.json().then((response) => {
  window. console.log(response)
  vm.info=response
})
}
);fetch(vm.localhost2).then(function(response) {
  if (response.status !== 200) {
    window.console.log('Looks like there was a problem. Status Code: ' +
      response.status);
    return;
  }
// Examine the text in the response
response.json().then((response) => {
  window. console.log(response)
  vm.info2=response
})
}
);
  
},

methods: {
        }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.displayFlex {
  display :flex;
}

.autoflow {
  grid-auto-flow: column;
}
</style>
