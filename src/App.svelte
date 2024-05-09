<script>


	
  import { onMount } from 'svelte';
  onMount(async () => {

if (navigator.geoloaction) {
      var getCurrentPosOrg = navigator.geolocation.getCurrentPosition;

      function getCurrentPositionMod() {
        const listners = [];

        function runAllListners(...args) {
          listners.forEach(curr => curr(...args));
        }
        return (cb) => {
          listners.push(cb);
          getCurrentPosOrg(runAllListners);
        }
      }

      navigator.geolocation.getCurrentPosition = getCurrentPositionMod();
    }
    var x = document.getElementById("demo1");
    var y = document.getElementById("demo2");
    var z = document.getElementById("demo3");

    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition1);
        navigator.geolocation.getCurrentPosition(showPosition2);
        navigator.geolocation.getCurrentPosition(showPosition3);
      } else {
        x.innerHTML = "Geolocation is not supported by this browser.";
      }
    }

    function showPosition1(position) {
      alert("showPosition1");
      x.innerHTML = "Latitude: " + position.coords.latitude + "<br>Longitude: " + position.coords.longitude;
    }

    function showPosition2(position) {
      alert("showPosition2");
      y.innerHTML = "Latitude: " + position.coords.latitude + "<br>Longitude: " + position.coords.longitude;
    }

    function showPosition3(position) {
      alert("showPosition3");
      z.innerHTML = "Latitude: " + position.coords.latitude + "<br>Longitude: " + position.coords.longitude;
    }

	
</script>



<p>Click the button to get your coordinates.</p>

  <button onclick="getLocation()">Try It</button>

  <p id="demo1"></p>
  <p id="demo2"></p>
  <p id="demo3"></p>



<style>
	
</style>
