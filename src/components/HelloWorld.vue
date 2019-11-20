<template>
  <div class="hello">
    <form action="http://localhost:3000/example" method="POST">
  First name: <input type="text" name="origin"><br>
  Last name: <input type="text" name="destination"><br>
 <button type="submit">Send to backend</button>
</form>
   <div v-for="item in info" :key="item.departureDate">
     {{item.origin}}--{{item.destination}}--{{item.price.total}}
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
  localhost: "http://localhost:3000",
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


  
 
// const call = new Promise( (resolve, reject) => {
// this.$loading(true)
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
// });
})

// asyncLoading(call).then(this.$loading(false)).catch(function(err) {
//     window.console.log('Fetch Error :-S', err, reject);
//   });

// return resolve

}
)
  
},

methods: {
        }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
