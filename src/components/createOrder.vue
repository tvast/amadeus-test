<template src="./createOrder.html"></template>


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
  width: 10%;
  margin: 20px auto 20px;
  padding: 10px 20px;
  font-size: 14px;
  background-color: #448aff;
  color: white;
  border: none;
  border-radius: 16px; 
}

.next:hover {
  background-color: #D52CAC;
}

 .md-progress-bar {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
  }
</style>

<script>
import { VueContentLoading,VclFacebook, VclInstagram } from 'vue-content-loading';
// import { validationMixin } from 'vuelidate'
  import {
    required,
    email,
    minLength,
    maxLength
  } from 'vuelidate/lib/validators'
// import Form from "./Form.vue"
export default {
  name: 'searchPrice',
  data: () => ({
  toggleInfo:false,

  form: {
  firstName: "theo",
  lastName: "vast",
  gender: null,
  age: null,
  email: "abc@gmail.com",},
  userSaved: false,
  sending: false,
  lastUser: null,
  menuVisible: false,
  components: {
  VclFacebook,
  VclInstagram,
  VueContentLoading,
  },
  selectedCountryDeparture: null,
  countriesDeparture: [
  'MAD',
  'PAR',
  'SYD',
  'BKK',
  ],
  selectedCountryArrival: null,
  countriesArrival: [
  'MAD',
  'PAR',
  'SYD',
  'BKK',
  ],
  localhost: "https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT,CITY&keyword=",
  info:{},
  info2:{},
  info3:{},
  token:"",
  localhost3: "http://localhost:3000/token",
  localhost2: "http://localhost:3000/flight",
  selectedDateDeparture :"2020-02-01",
  selectedDateArrival : "2020-02-27",
  mojsOptions : {
            count : 6,
            radius: { 15: 100 },
            origin: '100% 100%',
            degree: 360,
            children: {
              shape: 'polygon',
              fill: ['blue','white'],
              isSwirl:true,
              swirlSize: 10,
              swirlFrequency: 2,
              delay: 'stagger(0, 30)'
            }
          },
          selectedTravel:{},
          searchObject:""
  }),
  validations: {
      form: {
        firstName: {
          required,
          minLength: minLength(3)
        },
        lastName: {
          required,
          minLength: minLength(3)
        },
        age: {
          required,
          maxLength: maxLength(3)
        },
        gender: {
          required
        },
        email: {
          required,
          email
        }}},
computed : {
            
             
},

watch:{
			selectedTravel(){
				// alert('checkbox changed');
				return window.console.log(this.selectedTravel);}
			},

methods: {

	autocompleteCity(){
		window.console.log(this.selectedCountryDeparture+" "+this.selectedCountryArrival)
	},  getValidationClass (fieldName) {
		const field = this.form[fieldName]

		if (field) {
			return {
				'md-invalid': field.$invalid && field.$dirty
			}
		}
	},
	clearForm () {
		this.$v.$reset()
		this.form.firstName = null
		this.form.lastName = null
		this.form.age = null
		this.form.gender = null
		this.form.email = null
	},
	// saveUser () {
	// 	this.sending = true

 //        // Instead of this timeout, here you can call your API
 //        window.setTimeout(() => {
 //        this.lastUser = `${this.form.firstName} ${this.form.lastName}`
 //        this.userSaved = true
 //        this.sending = false
 //        this.clearForm()
 //        }, 1500)
 //    },
    validateUser () {
    //get info from flight
     window.console.log(this.selectedTravel)
	

	var vm=this;
	function isCherries(flight) { 
	return flight.id === vm.selectedTravel;
	}
	this.searchObject = this.info2.find(isCherries);
	window.console.log(this.searchObject);
    //get user info

    //generate request
    var requestCreateOrder={
  "data": {
    "type": "flight-order",
    "flightOffers": [this.searchObject],
    "travelers": [
      {
        "id": "1",
        "dateOfBirth": "1982-01-16",
        "name": {
          "firstName": this.form.firstName,
          "lastName": this.form.lastName
        },
        "gender": "MALE",
        "contact": {
          "emailAddress": this.form.email = null,
          "phones": [
            {
              "deviceType": "MOBILE",
              "countryCallingCode": "33",
              "number": "0665735114"
            }
          ]
        },
        "documents": [
          {
            "documentType": "PASSPORT",
            "birthPlace": "Madrid",
            "issuanceLocation": "Madrid",
            "issuanceDate": "2015-04-14",
            "number": "00000000",
            "expiryDate": "2025-04-14",
            "issuanceCountry": "ES",
            "validityCountry": "ES",
            "nationality": "ES",
            "holder": true
          }
        ]
      },
      
    ],
    "remarks": {
      "general": [
        {
          "subType": "GENERAL_MISCELLANEOUS",
          "text": "ONLINE BOOKING FROM INCREIBLE VIAJES"
        }
      ]
    },
    "ticketingAgreement": {
      "option": "DELAY_TO_CANCEL",
      "delay": "6D"
    },
    "contacts": [
      {
        "addresseeName": {
          "firstName": "PABLO",
          "lastName": "RODRIGUEZ"
        },
        "companyName": "INCREIBLE VIAJES",
        "purpose": "STANDARD",
        "phones": [
          {
            "deviceType": "LANDLINE",
            "countryCallingCode": "34",
            "number": "480080071"
          },
          {
            "deviceType": "MOBILE",
            "countryCallingCode": "33",
            "number": "480080072"
          }
        ],
        "emailAddress": "support@increibleviajes.es",
        "address": {
          "lines": [
            "Calle Prado, 16"
          ],
          "postalCode": "28014",
          "cityName": "Madrid",
          "countryCode": "ES"
        }
      }
    ]
  }
}
    //fetch node js api and send the object
let uriCreateOrder = "http://localhost:3000/flightCreateOrder"
let header= {'Content-Type': 'application/json'}
  fetch(uriCreateOrder, { method: 'POST',
   headers: header, 
  body: JSON.stringify(requestCreateOrder)
})
  .then((response) => {
     // var vm=this;
this.info3=response
  
  // Do something with the returned data.
});
  const uriAuth ="http://localhost:3000/flightcretaeorderget" 

fetch(uriAuth)
  .then((res) => {
     return res.json()
})
.then((json) => {
  window.console.log(json);
  this.info3=json;
  this.toggleInfo=true;

})
},

  letsFly() {
    this.info2="";
  let bodyDate = "departure="+this.selectedDateDeparture + "&"+"arrival="+this.selectedDateArrival+"&locationDeparture="+this.selectedCountryDeparture+"&locationArrival="+this.selectedCountryArrival;
   window.console.log(bodyDate)
  let headers= {
      // 'Content-Type': 'application/json'   
      'Content-Type': 'application/x-www-form-urlencoded',
     };
  let uriDate ="http://localhost:3000/date?" +bodyDate
  // let bodyDate2 = {
  //   departure: this.selectedDateDeparture,
  //   arrival:this.selectedDateArrival
  // }
  fetch(uriDate, { method: 'POST', 
   headers: headers, 
  body: bodyDate
})
  .then(() => {
     var vm=this;
fetch(vm.localhost3).then(function(response) {
// Examine the text in the response
response.json().then((response) => {
  window. console.log(response)
  vm.token=response
})
}
);
  
  // Do something with the returned data.
});
  const uriAuth ="http://localhost:3000/flightSearch" 

fetch(uriAuth)
  .then((res) => {
     return res.json()
})
.then((json) => {
  window.console.log(json);
  this.info2=json;
  this.toggleInfo=true;

})
},

getFLightPrice () {
 window.console.log(this.selectedTravel)
	//get the flight offer
	// productById (info2) { // function
 //      return productId => { // product by id
 //        return info2.id.find(product => product.id === productId)
 //        }
 //      }

 var vm=this;
function isCherries(flight) { 
  return flight.id === vm.selectedTravel;
}
this.searchObject = this.info2.find(isCherries);
window.console.log(this.searchObject); 

   this.info3="";
  
  let headers= {
      'Content-Type': 'application/json'   
      // 'Content-Type': 'JSON',
     };
  let uriDate ="http://localhost:3000/flightprice"
  // let bodyDate2 = {
  //   departure: this.selectedDateDeparture,
  //   arrival:this.selectedDateArrival
  // }
  fetch(uriDate, { method: 'POST', 
   headers: headers, 
  body: JSON.stringify(this.searchObject)
})
  .then(() => {
     // var vm=this;
fetch("http://localhost:3000/flightPriceget").then((res) => {
     return res.json()
})
.then((json) => {
  window.console.log(json);
  this.info3=json;

})
;
  
  // Do something with the returned data.
});
//   const uriAuth ="http://localhost:3000/flightPriceget" 

// fetch(uriAuth)
//   .then((res) => {
//      return res.json()
// })
// .then((json) => {
//   window.console.log(json);
//   this.info3=json;

// })
},
}


        

}
</script>
  
