---
title: "Weather Forecast"
date: 2024-09-16
# layout: "weather"
# ---

# This page displays weather forecasts and aurora predictions NON HTML VERSION.
type: landing

sections:
  - block: markdown
    design:
      columns: '1'
      css_style: 'text-align: center;'
    content:
      title: Forecasts & Weather
      text: |
        <p style="font-size: medium;">Due to the volatile nature of weather in Canberra, as well as the prime view Mount Stromlo Observatory has for certain astronomical events, I've collated some forecast tools here to avoid the need to check multiple apps/websites/widgets. These are implemented using free APIs, widgets, or in the case of some NOAA data, hard coded from their available image files. The dusk/dawn times are also hard coded as no simple API seems to exist. These calculations were taken from NOAA's Global Monitoring Labratory <a href="https://gml.noaa.gov/grad/solcalc/calcdetails.html">solar calculation details</a>. I will likely put the Python and/or Javascript code on github soon for anyone interest. Weather warnings are provided by BOM via <a href="https://www.willyweather.com.au">WillyWeather</a>.</p>

        {{< details title="Todo" >}}
        <p style="font-size: medium;"> Some things on this page still need to be done: trying brentq instead of bisection method for root finding (see <a href="https://www.bomberbot.com/mathematics/mastering-root-finding-algorithms-in-javascript-a-comprehensive-guide/">this</a> and <a href="https://gist.github.com/ryanspradlin/18c1010b7dd2d875284933d018c5c908">this</a>, check that the twilight calculator is working (gives different results to <a href="https://www.timeanddate.com/astronomy/australia/canberra">this</a>, and I also need to check if the days are correct -- ie does midnight in CBR cause the next day to tick over for javascript? Maybe just print out the day in the section title), implement some extra info from the AAT pages <a href="https://aat-ops.anu.edu.au/AATdatabase/met.html">here</a> and <a href="https://aat-ops.anu.edu.au/met/">here</a>, add solar images from the following links: https://www.swpc.noaa.gov/products/goes-solar-ultraviolet-imager-suvi#, https://services.swpc.noaa.gov/products/animations/suvi-primary-284.json, https://services.swpc.noaa.gov/images/animations/suvi/primary/304/, https://www.sws.bom.gov.au/, https://www.sws.bom.gov.au/Images/SOLROT/noscript/SOL_IMG_9.jpg?11, and maybe put in solar wind from https://www.swpc.noaa.gov/products/wsa-enlil-solar-wind-prediction. Flightradar widget from AirNav? Also, want to add a manual solar time calculator for given location. Also add video or at least link to last night's Stromlo video. I'd also like a moonrise calculator or a moon visibility curve.</p>
        {{< /details >}}

        <p style="font-size: medium;"> </p>
        <!-- Aurora update notification -->
        <div id="notification" style="display: none; position: fixed; top: 80px; left: 10px; background-color: rgba(0, 0, 0, 0.7); color: white; padding: 10px; border-radius: 5px; z-index: 1000;">
          New aurora forecast frame!
        </div>

        <!-- Clocks -->
        <div style="width:400px; margin:0 auto; margin-bottom:34px;">
          <div style="float:left;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/n57/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="float:right;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <!-- Twilight times -->
        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
          <p><strong>Twilight Times for Today</strong></p>
    
          <p>Astr. Dawn: <span id="aDaTod"></span></p>
          <p>Naut. Dawn: <span id="nDaTod"></span></p>
          <p>Civil Dawn: <span id="cDaTod"></span></p>
          <p>Sunrise: <span id="sunrTod"></span></p>
          <p>Sunset: <span id="sunsTod"></span></p>
          <p>Civil Dusk: <span id="cDuTod"></span></p>
          <p>Naut. Dusk: <span id="nDuTod"></span></p>
          <p>Astr. Dusk: <span id="aDuTod"></span></p>
        </div>

        <div style="width:620px; margin:0 auto; margin-bottom:20px;"></div>
          <p><strong>Twilight Times for Tomorrow</strong></p>
    
          <p>Astr. Dawn: <span id="aDaTom"></span></p>
          <p>Naut. Dawn: <span id="nDaTom"></span></p>
          <p>Civil Dawn: <span id="cDaTom"></span></p>
          <p>Sunrise: <span id="sunrTom"></span></p>
          <p>Sunset: <span id="sunsTom"></span></p>
          <p>Civil Dusk: <span id="cDuTom"></span></p>
          <p>Naut. Dusk: <span id="nDuTom"></span></p>
          <p>Astr. Dusk: <span id="aDuTom"></span></p>
        </div>

        <!-- WillyWeather forecast -->
        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
          <div style="width: 620px;">
            <iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75240" width="620" height="520" frameborder="0"  scrolling="no"></iframe><a style="margin: -20px 0 0 0;display: block;position: relative;height: 20px;text-indent: -9999em;z-index: 1" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">OConnor Weather</a>
          </div>
        </div>

        <!-- Windy Maps -->
        <div class="map-container" style="position: relative; width: 100%; max-width: 620px; margin-bottom: 20px; margin:0 auto; text-align: center;">

          <!-- Full-width Canberra Rain and Thunder-->
          <div style="width:620px; margin:0 auto; margin-bottom:20px;">
            <iframe width="620" height="620" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=rain&product=ecmwf&level=surface&lat=-35.604&lon=148.975&message=true" frameborder="0"></iframe>
          </div>
          
          <!-- Half-width Canberra weather radar and rain accumulation-->
          <div style="width:620px; margin:0 auto; margin-bottom:20px;">
            <div style="float:left;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=radar&product=radar&level=surface&lat=-35.604&lon=148.975&message=true" frameborder="0"></iframe>
            </div>
            <div style="float:right;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=rainAccu&product=ecmwf&level=surface&lat=-35.604&lon=148.975&message=true" frameborder="0"></iframe>
            </div>
            <div style="clear:both;"></div>
          </div>

          <!-- Half-width Canberra Wind and Wind gusts-->
          <div style="width:620px; margin:0 auto; margin-bottom:20px;">
            <div style="float:left;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=wind&product=ecmwf&level=surface&lat=-35.604&lon=148.975&message=true" frameborder="0"></iframe>
            </div>
            <div style="float:right;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=gust&product=ecmwf&level=surface&lat=-35.604&lon=148.975&message=true" frameborder="0"></iframe>
            </div>
            <div style="clear:both;"></div>
          </div>

          <!-- Full-width Aus satellite-->
          <div style="width:620px; margin:0 auto; margin-bottom:20px;">
            <iframe width="620" height="620" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=4&overlay=satellite&product=satellite&level=surface&lat=-27.917&lon=133.857&message=true" frameborder="0"></iframe>
          </div>

          <!-- Half-width Aus temperature and rain and thunder -->
          <div style="width:620px; margin:0 auto; margin-bottom:20px;">
            <div style="float:left;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=3&overlay=temp&product=ecmwf&level=surface&lat=-28.768&lon=133.945&message=true" frameborder="0"></iframe>
            </div>
            <div style="float:right;">
              <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=3&overlay=rain&product=ecmwf&level=surface&lat=-28.768&lon=133.945&message=true" frameborder="0"></iframe>
            </div>
            <div style="clear:both;"></div>
          </div>

          <div class="interaction-blocker" id="blocker" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.1); z-index: 10;"></div>
        </div>

        <label style="position: relative; display: inline-block; width: 34px; height: 20px; margin-bottom: 20px;">
          <input type="checkbox" id="toggleInteraction" style="opacity: 0; width: 0; height: 0;"/>
          <span style="
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 20px;
          "></span>
          <span style="
            position: absolute;
            background-color: white;
            border-radius: 50%;
            height: 16px;
            width: 16px;
            left: 2px;
            bottom: 2px;
            transition: .4s;
            transform: translateX(0);
          "></span>
        </label>

        

        <p><strong>Space Weather</strong></p>

        <!-- Aurora Alert Data -->
        <div id="aurora-alert-info" style="background-color: rgb(188, 0, 0); color: white; border: 1px solid white; padding: 2px; margin: 0px auto; width: 100%; font-size: small; line-height: 1.2em;">
          <p>Loading Aurora Alert data...</p>
        </div>

        <!-- Aurora Watch Data -->
        <div id="aurora-watch-info" style="background-color: black; color: white; border: 1px solid white; padding: 2px; margin: 0px auto; width: 100%; font-size: small; line-height: 1.2em; margin-bottom:20px;">
          <p>Loading Aurora Watch data...</p>
        </div>

        <!-- NOAA SH Aurora Forecast -->
        <div class="animation" id="auroraAnimation" style="width:620px; margin:0 auto; text-align: center; margin-bottom:20px;">
          <canvas id="auroraCanvas" title="Click to view full screen" height="620" width="620" style="max-width: 620px;"></canvas>
          <div class="animationToolbar" style="max-width: 620px; display: flex; align-items: center; margin-top: 10px; justify-content: center;">
            <!-- Play/Pause Button -->
            <button id="startButton" class="animationButton startButton" style="border: 1px solid white; background-color: black; color: white; width: 80px; height: 40px; margin-right: 10px; cursor: pointer; transition: background-color 0.3s, color 0.3s, transform 0.2s;" title="Play or Pause">Play</button>
            <!-- Progress Bar -->
            <div id="progressContainer" style="position: relative; width: 100%; max-width: 500px; flex-grow: 1; margin-left: 10px;">
              <input type="range" id="progressBar" value="0" max="100" style="width: 100%; -webkit-appearance: none; background: #ddd; height: 6px; border-radius: 3px;">
            </div>
          </div>
        </div>

        {{< details title="AAT Information" >}}
          <p><strong>AAT Cams</strong></p>

          <!-- AAT SkyCam -->
          <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
            <img id="AATSkyCam" src="https://aat-ops.anu.edu.au/skycam/telescope/telescope.png" alt="AAT Skycam Image" style="width: 100%; height: auto;">
            <button class="refresh-button" onclick="refreshImage('AATSkyCam')" style="position: absolute;bottom: 5px; right: 5px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 2px; border-radius: 5px; cursor: pointer; z-index: 10; font-size: small;">Refresh</button>
          </div>

          <!-- AAT Pano -->
          <!-- Doesn't work anymore. Fingers crossed for a replacement sky cam soon.
          <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
            <img id="AATPano" src="https://aat-ops.anu.edu.au/skycam/telescope/horizon.jpg" alt="AAT Pano Image" style="width: 100%; height: auto;">
            <button class="refresh-button" onclick="refreshImage('AATPano')" style="position: absolute;bottom: 5px; right: 5px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 2px; border-radius: 5px; cursor: pointer; z-index: 10; font-size: small;">Refresh</button>
          </div>
          -->
        {{< /details >}}
        

        <p><strong>MSO Cams</strong></p>

        <!-- MSO SkyCam -->
        <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
          <img id="MSOSkyCam" src="https://www.mso.anu.edu.au/msoallsky/msoskycam.jpg" alt="MSO Skycam Image" style="width: 100%; height: auto;">
          <button class="refresh-button" onclick="refreshImage('MSOSkyCam')" style="position: absolute;bottom: 5px; right: 5px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 2px; border-radius: 5px; cursor: pointer; z-index: 10; font-size: small;">Refresh</button>
        </div>

        <!-- MSO Pano -->
        <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
          <img id="MSOPano" src="https://www.mso.anu.edu.au/msoallsky/panorama.jpg" alt="MSO Pano Image" style="width: 100%; height: auto;">
          <button class="refresh-button" onclick="refreshImage('MSOPano')" style="position: absolute;bottom: 5px; right: 5px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 2px; border-radius: 5px; cursor: pointer; z-index: 10; font-size: small;">Refresh</button>
        </div>

        <!-- MSO Western Horizon Cam -->
        <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
          <img id="MSOHorizon" src="https://www.mso.anu.edu.au/~brad/brightsky/reynolds/latest.jpg" alt="MSO Western Horizon Image" style="width: 100%; height: auto;">
          <button class="refresh-button" onclick="refreshImage('MSOHorizon')" style="position: absolute;bottom: 5px; right: 5px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 2px; border-radius: 5px; cursor: pointer; z-index: 10; font-size: small;">Refresh</button>
        </div>

        <!-- weather warnings -->
        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75237" type="application/javascript"></script>

        <!-- SCRIPTS -->

        <!-- NASA API script -->
        <script>
          async function fetchNASAData() {
            const apiKey = '7fraiXp4qSUvpkgGhfImAxLjmZ6YqAm8pFwe0PiI';
            const startDate = '2024-09-16'; // Adjust this to the current or desired date
            const endDate = '2024-09-23'; // Adjust as needed
            const url = `https://api.nasa.gov/neo/rest/v1/feed?start_date=${startDate}&end_date=${endDate}&api_key=${apiKey}`;

            try {
              const response = await fetch(url);
              const data = await response.json();

              // Display NASA data
              const element = document.getElementById('nasa-neo-info');
              element.innerHTML = `<p>Near-Earth Objects from ${startDate} to ${endDate}:</p>`;

              data.near_earth_objects[startDate].forEach(neo => {
                element.innerHTML += `<p>Object: ${neo.name} - Diameter: ${neo.estimated_diameter.kilometers.estimated_diameter_max} km</p>`;
              });
              
            } catch (error) {
              console.error('Error fetching data:', error);
            }
          }

        </script>

        <!-- POST request to get aurora alert -->
        <script>
          async function fetchAuroraAlert() {
            const url = 'https://sws-data.sws.bom.gov.au/api/v1/get-aurora-alert';
            const apiKey = 'e7aac3e9-ed4d-4b9a-87e8-204d6a5ab680';
            
            try {
              const response = await fetch(url, {
                method: 'POST',
                headers: {
                  'Content-Type': 'application/json',
                },
                body: JSON.stringify({ api_key: apiKey })
              });
              
              const data = await response.json();
              const alertContainer = document.getElementById('aurora-alert-info');

              if (data.data.length > 0) {
                const alert = data.data[0];
                alertContainer.innerHTML = `
                  <p><strong>Aurora Alert:</strong> issued at ${alert.start_time}</p>
                  <p>K index of ${alert.k_aus}, ${alert.lat_band} latitude band. ${alert.description}</p>
                `;
              } else {
                alertContainer.innerHTML = `<p>No active aurora alerts at this time.</p>`;
              }
            } catch (error) {
              console.error('Error fetching Aurora Alert data:', error);
              document.getElementById('aurora-alert-info').innerHTML = `<p>Error loading aurora alert data.</p>`;
            }
          }

        </script>

        <!-- POST request to get aurora watch -->
        <script>
          async function fetchAuroraWatch() {
            const url = 'https://sws-data.sws.bom.gov.au/api/v1/get-aurora-watch';
            const apiKey = 'e7aac3e9-ed4d-4b9a-87e8-204d6a5ab680';
            
            try {
              const response = await fetch(url, {
                method: 'POST',
                headers: {
                  'Content-Type': 'application/json',
                },
                body: JSON.stringify({ api_key: apiKey })
              });
              
              const data = await response.json();
              const watchContainer = document.getElementById('aurora-watch-info');

              if (data.data.length > 0) {
                const watch = data.data[0];
                watchContainer.innerHTML = `
                  <p><strong>Aurora Watch ${watch.start_date} -- ${watch.end_date}</strong></p>
                  <p>Issued at ${watch.issue_time}</p>
                  <p>K index of ${watch.k_aus}, ${watch.lat_band} latitude band.</p>
                  <p>Dominant cause of ${watch.cause}. ${watch.comments}</p>
                `;
              } else {
                watchContainer.innerHTML = `<p>No active aurora watch at this time.</p>`;
              }
            } catch (error) {
              console.error('Error fetching Aurora Watch data:', error);
              document.getElementById('aurora-watch-info').innerHTML = `<p>Error loading aurora watch data.</p>`;
            }
          }

        </script>

        <!-- NOAA aurora forecast (southern hemisphere) animation -->
        <script>
          const canvas = document.getElementById('auroraCanvas');
          const ctx = canvas.getContext('2d');
          let images = [];
          let imageTimes = [];
          let currentFrame = 0;
          let isPlaying = false;
          let animationInterval;
          const baseURL = 'https://services.swpc.noaa.gov'; // Base URL for images

          // Function to fetch and process the animation data
          async function fetchAnimationData() {
            try {
              const response = await fetch('https://services.swpc.noaa.gov/products/animations/ovation_south_24h.json');
              const data = await response.json();
              
              // Map the images and time tags from the JSON
              images = data.map(item => {
                const img = new Image();
                img.src = baseURL + item.url; // Construct the full URL
                imageTimes.push(new Date(item.time_tag)); // Store time tags for comparison
                return img;
              });

              // Ensure all images are loaded before starting the animation
              let loadedImages = 0;
              images.forEach(img => {
                img.onload = () => {
                  loadedImages++;
                  if (loadedImages === images.length) {
                    console.log('All images loaded');
                    displayFirstImage(); // Display the first image on page load
                  }
                };
                img.onerror = () => {
                  console.error('Error loading image:', img.src);
                };
              });
            } catch (error) {
              console.error('Error fetching animation data:', error);
            }
          }

          // Display the first image
          function displayFirstImage() {
            if (images.length > 0) {
              ctx.drawImage(images[0], 0, 0, canvas.width, canvas.height);
            }
          }

          // Draw each frame
          function drawFrame() {
            if (images.length > 0) {
              ctx.clearRect(0, 0, canvas.width, canvas.height);
              ctx.drawImage(images[currentFrame], 0, 0, canvas.width, canvas.height);
              document.getElementById('progressBar').value = (currentFrame / (images.length - 1)) * 100;
              currentFrame = (currentFrame + 1) % images.length;
            }
          }

          // Start the animation
          function startAnimation() {
            if (!isPlaying) {
              isPlaying = true;
              animationInterval = setInterval(drawFrame, 100); // Adjust speed as necessary
              document.getElementById('startButton').innerText = 'Pause';
            }
          }

          // Stop the animation
          function stopAnimation() {
            isPlaying = false;
            clearInterval(animationInterval);
            document.getElementById('startButton').innerText = 'Play';
          }

          // Toggle Play/Pause
          document.getElementById('startButton').addEventListener('click', function() {
            if (isPlaying) {
              stopAnimation();
            } else {
              startAnimation();
            }
          });

          // Update frame based on progress bar
          document.getElementById('progressBar').addEventListener('input', function(event) {
            if (images.length > 0) {
              currentFrame = Math.round((event.target.value / 100) * (images.length - 1));
              ctx.clearRect(0, 0, canvas.width, canvas.height);
              ctx.drawImage(images[currentFrame], 0, 0, canvas.width, canvas.height);
            }
          });

          // Check if new aurora forecast frames are available by comparing timestamps
          async function checkForNewFrames() {
            const response = await fetch('https://services.swpc.noaa.gov/products/animations/ovation_south_24h.json');
            const data = await response.json();
            const latestFrameTime = new Date(data[data.length - 1].time_tag);

            // If the latest frame is newer than the last loaded frame, reload the animation and show notification
            if (latestFrameTime > imageTimes[imageTimes.length - 1]) {
              console.log('New frames available. Reloading animation...');
              await fetchAnimationData(); // Fetch new images and update the animation
              showNotification(); // Show notification
            } else {
              console.log('No new frames available.');
            }
          }

          // Check for new frames every 5 minutes
          setInterval(checkForNewFrames, 5 * 60 * 1000); // 15 minutes interval

          // Show notification for new frames
          function showNotification() {
            const notification = document.getElementById('notification');
            notification.style.display = 'block'; // Show the notification
            setTimeout(() => {
              notification.style.display = 'none'; // Hide after 5 seconds
            }, 10000); // Notification duration in milliseconds (5 seconds)
          }

          // Initial load of the animation
          fetchAnimationData();
        </script>

        <script>
        // Initial state: interaction is blocked
        let interactionEnabled = false;

        document.getElementById('toggleInteraction').addEventListener('change', function() {
            const blocker = document.getElementById('blocker');
            const slider = this.nextElementSibling;
            const knob = slider.nextElementSibling;

            if (this.checked) {
                // Enable interaction (hide the blocker)
                blocker.style.display = 'none';
                this.nextElementSibling.style.backgroundColor = '#BC0000'; // Change background color when enabled
                knob.style.transform = 'translateX(14px)'; // Move knob to the right
                this.nextElementSibling.style.transition = 'background-color 0.4s';
                knob.style.transition = 'transform 0.4s';
                this.nextElementSibling.style.borderRadius = '20px';
            } else {
                // Disable interaction (show the blocker)
                blocker.style.display = 'block';
                this.nextElementSibling.style.backgroundColor = '#ccc'; // Change background color when disabled
                knob.style.transform = 'translateX(0)'; // Move knob to the left
                this.nextElementSibling.style.transition = 'background-color 0.4s';
                knob.style.transition = 'transform 0.4s';
                this.nextElementSibling.style.borderRadius = '20px';
            }
            
            // Toggle state
            interactionEnabled = !interactionEnabled;
        });
        </script>

        <!-- Twilight calculator -->
        <script>
          class TwilightCalculator {
            constructor(lat = -35.2802, long = 149.1310, timeZone = 10) {
              this.lat = lat;
              this.long = long;
              this.timeZone = timeZone;
            }

            solarElevation(minPastMidnight, date, offset = 0) {
              const julianDay = Math.floor(date.getTime() / 86400000) + 2440587.5;
              const julianDate = julianDay - this.timeZone / 24 + minPastMidnight / 1440;
              const julianCentury = (julianDate - 2451545) / 36525;

              const GMLS = (280.46646 + julianCentury * (36000.76983 + julianCentury * 0.0003032)) % 360;
              const GMAS = 357.52911 + julianCentury * (35999.05029 - 0.0001537 * julianCentury);
              const eccentEarthOrbit = 0.016708634 - julianCentury * (0.000042037 + 0.0000001267 * julianCentury);

              const sunEqOfCtr = Math.sin(this.degToRad(GMAS)) * (1.914602 - julianCentury * (0.004817 + 0.000014 * julianCentury)) +
                Math.sin(this.degToRad(2 * GMAS)) * (0.019993 - 0.000101 * julianCentury) +
                Math.sin(this.degToRad(3 * GMAS)) * 0.000289;

              const sunTrueLong = GMLS + sunEqOfCtr;
              const sunAppLong = sunTrueLong - 0.00569 - 0.00478 * Math.sin(this.degToRad(125.04 - 1934.136 * julianCentury));

              const meanObliqEcliptic = 23 + (26 + (21.448 - julianCentury * (46.815 + julianCentury * (0.00059 - julianCentury * 0.001813))) / 60) / 60;
              const obliqCorr = meanObliqEcliptic + 0.00256 * Math.cos(this.degToRad(125.04 - 1934.136 * julianCentury));

              const sunDec = this.radToDeg(Math.asin(Math.sin(this.degToRad(obliqCorr)) * Math.sin(this.degToRad(sunAppLong))));

              const varY = Math.tan(this.degToRad(obliqCorr / 2)) ** 2;
              const eqOfTime = 4 * this.radToDeg(varY * Math.sin(2 * this.degToRad(GMLS)) - 
                2 * eccentEarthOrbit * Math.sin(this.degToRad(GMAS)) + 
                4 * eccentEarthOrbit * varY * Math.sin(this.degToRad(GMAS)) * Math.cos(2 * this.degToRad(GMLS)) - 
                0.5 * varY ** 2 * Math.sin(4 * this.degToRad(GMLS)) - 
                1.25 * eccentEarthOrbit ** 2 * Math.sin(2 * this.degToRad(GMAS)));

              let TST = (minPastMidnight + eqOfTime + 4 * this.long - 60 * this.timeZone) % 1440;
              let hourAngle = (TST / 4 < 0) ? TST / 4 + 180 : TST / 4 - 180;

              const solarZenithAngle = this.radToDeg(Math.acos(Math.sin(this.degToRad(this.lat)) * Math.sin(this.degToRad(sunDec)) + 
                Math.cos(this.degToRad(this.lat)) * Math.cos(this.degToRad(sunDec)) * Math.cos(this.degToRad(hourAngle))));

              let solarElevationAngle = 90 - solarZenithAngle;

              // Atmospheric correction
              let atmCorr = 0;
              if (solarElevationAngle <= -0.575) {
                atmCorr = (-20.772 / Math.tan(this.degToRad(solarZenithAngle))) / 3600;
              } else if (solarElevationAngle <= 5) {
                atmCorr = (1735 + solarElevationAngle * (-518.2 + solarElevationAngle * (103.4 + solarElevationAngle * (-12.79 + solarElevationAngle * 0.711)))) / 3600;
              } else if (solarElevationAngle <= 85) {
                atmCorr = (58.1 / Math.tan(this.degToRad(solarElevationAngle)) - 0.07 / Math.tan(this.degToRad(solarElevationAngle)) ** 3 + 0.000086 / Math.tan(this.degToRad(solarElevationAngle)) ** 5) / 3600;
              }
                
              return solarElevationAngle + atmCorr + offset;
            }

            degToRad(deg) {
                return deg * Math.PI / 180;
            }

            radToDeg(rad) {
                return rad * 180 / Math.PI;
            }

            minToTime(mins) {
                const hour = Math.floor(mins / 60);
                const minute = Math.floor(mins % 60);
                const second = Math.floor(((mins % 60) * 60) % 60);
                return { hour, minute, second };
            }

            brentq(func, a, b, args) {
                // Implement a root-finding algorithm here. In practice, Brent's method needs to be ported
                // or use an existing JavaScript library for numerical solving.
                // For simplicity, this part will need to be handled carefully or with a library.
            }

            bisection(func, a, b, tol = 1e-6, maxIter = 100, ...args) {
              // Check if the initial interval is valid
              if (func(a, ...args) * func(b, ...args) > 0) {
                throw new Error("Invalid initial interval");
              }

              for (let i = 0; i < maxIter; i++) {
                // Compute the midpoint
                const c = (a + b) / 2;
                
                // Check if the function at the midpoint is close enough to 0 (root found)
                if (Math.abs(func(c, ...args)) < tol) {
                  return c;
                }
                
                // Update the interval
                if (func(a, ...args) * func(c, ...args) < 0) {
                  b = c;  // Root is between a and c
                } else {
                  a = c;  // Root is between c and b
                }
              }

              throw new Error("Exceeded maximum iterations");
            }


            getTwilights(date) {
                // Dummy implementation for the twilight times using brentq placeholder
                const astrDawn = this.bisection(this.solarElevation.bind(this), 0.0, 720.0, 1e-6, 100, date, 18);
                const nautDawn = this.bisection(this.solarElevation.bind(this), 0.0, 720.0, 1e-6, 100, date, 12);
                const civDawn = this.bisection(this.solarElevation.bind(this), 0.0, 720.0, 1e-6, 100, date, 6);
                const sunrise = this.bisection(this.solarElevation.bind(this), 0.0, 720.0, 1e-6, 100, date, 0);

                const sunset = this.bisection(this.solarElevation.bind(this), 720.0, 1440.0, 1e-6, 100, date, 0);
                const civDusk = this.bisection(this.solarElevation.bind(this), 720.0, 1440.0, 1e-6, 100, date, 6);
                const nautDusk = this.bisection(this.solarElevation.bind(this), 720.0, 1440.0, 1e-6, 100, date, 12);
                const astrDusk = this.bisection(this.solarElevation.bind(this), 720.0, 1440.0, 1e-6, 100, date, 18);

                /*
                const astrDawn = this.brentq(this.solarElevation.bind(this), 0.0, 720.0, [date, 18]);
                const nautDawn = this.brentq(this.solarElevation.bind(this), 0.0, 720.0, [date, 12]);
                const civDawn = this.brentq(this.solarElevation.bind(this), 0.0, 720.0, [date, 6]);
                const sunrise = this.brentq(this.solarElevation.bind(this), 0.0, 720.0, [date]);

                const sunset = this.brentq(this.solarElevation.bind(this), 720.0, 1440.0, [date]);
                const civDusk = this.brentq(this.solarElevation.bind(this), 720.0, 1440.0, [date, 6]);
                const nautDusk = this.brentq(this.solarElevation.bind(this), 720.0, 1440.0, [date, 12]);
                const astrDusk = this.brentq(this.solarElevation.bind(this), 720.0, 1440.0, [date, 18]);
                */

                return [this.minToTime(astrDawn), this.minToTime(nautDawn), this.minToTime(civDawn), this.minToTime(sunrise), this.minToTime(sunset), this.minToTime(civDusk), this.minToTime(nautDusk), this.minToTime(astrDusk)];
            }
        }

        document.addEventListener('DOMContentLoaded', function() {
          // Create an instance of TwilightCalculator
          const calculator = new TwilightCalculator();

          // Get the current date
          const today = new Date();
          const tomorrow = new Date(today);  // Create a copy of today's date
          tomorrow.setDate(today.getDate() + 1);  // Add 1 day to the date

          // Call the getTwilights function
          const twilightTimes = calculator.getTwilights(today);
          const tomorrowTimes = calculator.getTwilights(tomorrow)

          // Extract each time from the result and format it
          // const formatTime = (time) => `${time.hour.toString().padStart(2, '0')}:${time.minute.toString().padStart(2, '0')}:${time.second.toString().padStart(2, '0')}`;

          const isDaylightSaving = (date) => {
            const jan = new Date(date.getFullYear(), 0, 1).getTimezoneOffset();
            const jul = new Date(date.getFullYear(), 6, 1).getTimezoneOffset();
            return date.getTimezoneOffset() < Math.max(jan, jul);
          };

          const formatTime = (time, date) => {
            let hours = time.hour;

            // Check if daylight saving time is active on the given date
            if (isDaylightSaving(date)) {
              hours += 1; // Adjust for daylight savings
            }

            return `${hours.toString().padStart(2, '0')}:${time.minute.toString().padStart(2, '0')}:${time.second.toString().padStart(2, '0')}`;
          };

          // Get the twilight times and inject them into HTML
          document.getElementById('aDaTod').innerText = formatTime(twilightTimes[0], today);
          document.getElementById('nDaTod').innerText = formatTime(twilightTimes[1], today);
          document.getElementById('cDaTod').innerText = formatTime(twilightTimes[2], today);
          document.getElementById('sunrTod').innerText = formatTime(twilightTimes[3], today);
          document.getElementById('sunsTod').innerText = formatTime(twilightTimes[4], today);
          document.getElementById('cDuTod').innerText = formatTime(twilightTimes[5], today);
          document.getElementById('nDuTod').innerText = formatTime(twilightTimes[6], today);
          document.getElementById('aDuTod').innerText = formatTime(twilightTimes[7], today);

          document.getElementById('aDaTom').innerText = formatTime(tomorrowTimes[0], tomorrow);
          document.getElementById('nDaTom').innerText = formatTime(tomorrowTimes[1], tomorrow);
          document.getElementById('cDaTom').innerText = formatTime(tomorrowTimes[2], tomorrow);
          document.getElementById('sunrTom').innerText = formatTime(tomorrowTimes[3], tomorrow);
          document.getElementById('sunsTom').innerText = formatTime(tomorrowTimes[4], tomorrow);
          document.getElementById('cDuTom').innerText = formatTime(tomorrowTimes[5], tomorrow);
          document.getElementById('nDuTom').innerText = formatTime(tomorrowTimes[6], tomorrow);
          document.getElementById('aDuTom').innerText = formatTime(tomorrowTimes[7], tomorrow);

          });
        </script>

        <!-- Image refresh script -->
        <script>
          function refreshImage(imageId) {
              const img = document.getElementById(imageId);
              img.src = img.src.split('?')[0] + `?timestamp=${new Date().getTime()}`;
          }
        </script>

        <script>
        window.onload = function() {
          fetchAuroraAlert();
          fetchAuroraWatch();
          fetchNASAData();
        }
        </script>
---