  <template>

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
      <!-- <button class="flights button">Flights</button> -->
      <!-- <button class="Hotels button">Hotels</button>
      <button class ="Packages button">Packages</button> -->
    </div>
   <div class="row1">
    <div class="locations from-location1">
     <md-autocomplete @input="autocompleteCity" v-model="selectedCountry" :md-options="countries">
      <label>Departure</label>
    </md-autocomplete>
    </div>
    <div class="locations to-location1">
      <md-autocomplete @input="autocompleteCity" v-model="selectedCountry" :md-options="countries">
      <label>Arrival</label>
    </md-autocomplete>
    </div>
  </div>
    <div class="row2">
      <div class="dates depart">
        <label class="depart-date" for="depart">Departure:</label>
        <md-datepicker v-model="selectedDate" />
      </div>
      <div class="dates return">
        <label class="returning-date" for="return">Return:</label>
        <md-datepicker v-model="selectedDate" />   
      </div>
    </div>
    <div class="next-button">
    <button class="next" value="submit">Let's Fly!</button>
      </div>
    </form>
  </main>

</template>

<script>


export default {
  name: 'Form',
  
}
</script>

<style>

</style>