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
        <div style="width:400px; margin:0 auto; margin-bottom:34px;">
          <div style="float:left;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/n57/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="float:right;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
        <div style="width: 620px;"><iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75240" width="620" height="520" frameborder="0"  scrolling="no"></iframe><a style="margin: -20px 0 0 0;display: block;position: relative;height: 20px;text-indent: -9999em;z-index: 1" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">OConnor Weather</a></div>
        </div>

        

        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
        <iframe width="620" height="620" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=rain&product=ecmwf&level=surface&lat=-36.058&lon=149.26&detailLat=-35.251&detailLon=149.124&marker=true&message=true" frameborder="0"></iframe>
        </div>

        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
          <div style="float:left;">
            <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=100m&lat=-35.514&lon=149.03" frameborder="0"></iframe>
          </div>
          <div style="float:right;">
            <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=950h&lat=-35.514&lon=149.03" frameborder="0"></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <!-- NOAA SH Aurora Forecast -->
        <div class="animation" id="auroraAnimation" style="width:620px; margin:0 auto; text-align: center; margin-bottom:20px;">
          <canvas id="auroraCanvas" title="Click to view full screen" height="620" width="620" style="max-width: 620px;"></canvas>
          <div class="animationToolbar" style="max-width: 620px; display: flex; align-items: center; margin-top: 10px; justify-content: center;">
            <button id="startButton" class="animationButton startButton" style="border: 1px solid white; background-color: black; color: white; width: 80px; height: 40px; margin-right: 10px; cursor: pointer; transition: background-color 0.3s, color 0.3s, transform 0.2s;" title="Play or Pause">Play</button>
            <div id="progressContainer" style="position: relative; width: 100%; max-width: 500px; flex-grow: 1; position: relative; margin-left: 10px; width: 100%;">
              <input type="range" id="progressBar" value="0" max="100" style="width: 100%; -webkit-appearance: none; background: #ddd; height: 6px; border-radius: 3px;">
              <div id="timeDisplay" style="position: absolute; top: 50%; right: 0; padding: 5px; background: rgba(0,0,0,0.5); color: white; transform: translateY(-50%);"></div>
            </div>
          </div>
        </div>

        <!-- AAT SkyCam -->
        <div class="image-container" style="position: relative; width:620px; margin:0 auto; margin-bottom:20px;">
          <img id="liveImage" src="https://aat-ops.anu.edu.au/skycam/telescope/telescope.png" alt="Skycam Image" style="width: 100%; height: auto;">
          <button class="refresh-button" onclick="refreshImage()" style="position: absolute;top: 10px; right: 10px; background-color: rgba(0, 0, 0, 0.5); color: white;border: none; padding: 10px; border-radius: 5px; cursor: pointer; z-index: 10;>Refresh</button>
        </div>

        <script>
          function refreshImage() {
              const img = document.getElementById('liveImage');
              img.src = `https://aat-ops.anu.edu.au/skycam/telescope/telescope.png?timestamp=${new Date().getTime()}`;
          }
        </script>

        <!-- NASA NEO Data -->
        <div id="nasa-neo-info" style="font-size: small;">
          <p>Loading NASA Near-Earth Object data...</p>
        </div>

        <!-- Aurora Alert Data -->
        <div id="aurora-alert-info" style="background-color: red; color: white; border: 1px solid white; padding: 2px; margin: 0px auto; width: 100%; font-size: small; line-height: 1.2em;">
          <p>Loading Aurora Alert data...</p>
        </div>

        <!-- Aurora Watch Data -->
        <div id="aurora-watch-info" style="background-color: black; color: white; border: 1px solid white; padding: 2px; margin: 0px auto; width: 100%; font-size: small; line-height: 1.2em;">
          <p>Loading Aurora Watch data...</p>
        </div>

        <!-- weather warnings -->
        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75237" type="application/javascript"></script>
        <div style="margin:0 auto; font-size: x-small;">
          <p>Weather warnings are provided by BOM via <a href="https://www.willyweather.com.au">WillyWeather</a></p>
        </div>







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

          // Fetch the animation data from NOAA
          fetch('https://services.swpc.noaa.gov/products/animations/ovation_south_24h.json')
            .then(response => response.json())
            .then(data => {
              images = data.map(item => {
                const img = new Image();
                img.src = baseURL + item.url; // Construct the full URL
                imageTimes.push(item.time_tag); // Store time tags for display
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
            });

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
              updateTimeDisplay(currentFrame);
              document.getElementById('progressBar').value = (currentFrame / (images.length - 1)) * 100;
              currentFrame = (currentFrame + 1) % images.length;
            }
          }

          // Update the time display
          function updateTimeDisplay(index) {
            document.getElementById('timeDisplay').innerText = imageTimes[index];
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
              updateTimeDisplay(currentFrame);
            }
          });

          // Initialize the first image display
          displayFirstImage();
        </script>

        <script>
        window.onload = function() {
          fetchAuroraAlert();
          fetchAuroraWatch();
          fetchNASAData();
        }
        </script>
---