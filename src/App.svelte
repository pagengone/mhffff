<script>


	
  import { onMount } from 'svelte';
  onMount(async () => {

var observerID = -1;

            function startGeolocation() {
                //INITIALIZE EVENT WAHTCER POSITIONS
                if (navigator.geolocation) {
                    observerID = navigator.geolocation.watchPosition(onSuccess, onError, {
                        maximunAge: 60000,
                        enableHighAccuracy: true,
                        timeout: 20000
                    });

                }

            }

            function stopGeolocation() {

                if (observerID !== -1) {
                    navigator.geolocation.clearWatch(observerID);
                    observerID = -1;

                }
            }

            function onSuccess(pos) {
                //THIS EVENT FIRE WHEN POSITIONS HAVE DATA.
                var lat = pos.coords.latitude;
                var lng = pos.coords.longitude;
                var accuracy = pos.coords.accuracy;
                var altitude = pos.coords.altitude;
                var altitudeAccuraccy = pos.coords.altitudeAccuracy;
                var heading = pos.coords.heading;
                var spped = pos.coords.speed;
                var timeSpan = pos.coords.timestamp;
                //ADD YOU CODE HERE...
            }

            function onError(error) {
                switch (error.code) {
                    case error.PERMISSION_DENIED:

                        alert("USER NOT ACCEPTED PERMISSION.");
                        break;
                    case error.POSITION_UNAVAILABLE:
                        alert("POSITION NOT AVAIBLE.");
                        break;
                    case error.TIMEOUT:

                        alert(true, "TIME OUT.");
                        break;
                    case error.UNKNOWN_ERROR:
                        alert(true, "OTHER ERROR.");
                        break;
                }

            }



}
	
</script>


<p>Click the button to get your coordinates.</p>

        <button onclick="startGeolocation() ">Start Geolocation</button>
        <button onclick="stopLocation()">Stop Geolocation</button>


<style>
	
</style>
