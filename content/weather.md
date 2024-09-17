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
        <div style="width:400px; margin:0 auto; margin-bottom:20px;">
          <div style="float:left;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/n57/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="float:right;">
            <iframe src="https://free.timeanddate.com/clock/i9jtr4t7/tlau/fs20/fcfff/tc111/bacfff/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="166" height="60"></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <div style="width:620px; margin:0 auto; margin-bottom:20px;">
        <div style="width: 620px;"><iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75239" width="620" height="520" frameborder="0"  scrolling="no"></iframe><a style="margin: -20px 0 0 0;position: relative;text-indent: -9999em;display: block;z-index: 1;height: 20px" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">OConnor weather info</a></div>
        </div>

        <div style="margin-bottom:20px;">
        <iframe width="620" height="620" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=rain&product=ecmwf&level=surface&lat=-36.058&lon=149.26&detailLat=-35.251&detailLon=149.124&marker=true&message=true" frameborder="0"></iframe>
        </div>

        <div style="width:620px; margin:0 auto;">
          <div style="float:left;">
            <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=100m&lat=-35.514&lon=149.03" frameborder="0"></iframe>
          </div>
          <div style="float:right;">
            <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=950h&lat=-35.514&lon=149.03" frameborder="0"></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <!-- NASA NEO Data -->
        <div id="nasa-neo-info">
          <p>Loading NASA Near-Earth Object data...</p>
        </div>

        <!-- Aurora Alert Data -->
        <div id="aurora-alert-info">
          <p>Loading Aurora Alert data...</p>
        </div>

        <!-- weather warnings -->
        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75237" type="application/javascript"></script>
        <small>Weather warnings are provided by BOM via <a href="https://www.willyweather.com.au">WillyWeather</a></small>

        <!-- NASA API script -->
        <script>
          async function fetchNASAData() {
            const apiKey = '7fraiXp4qSUvpkgGhfImAxLjmZ6YqAm8pFwe0PiI'; // Replace with your actual API key
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

          // Call the function when the page loads
          window.onload = fetchNASAData;
        </script>

        <!-- POST request to get aurora alert -->
        <script>
          async function fetchAuroraAlert() {
            const url = 'https://sws-data.sws.bom.gov.au/api/v1/get-aurora-alert';
            const apiKey = 'e7aac3e9-ed4d-4b9a-87e8-204d6a5ab680'; // Use the provided API key
            
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
                  <p><strong>Aurora Alert:</strong></p>
                  <p>Start Time: ${alert.start_time}</p>
                  <p>Valid Until: ${alert.valid_until}</p>
                  <p>K Index: ${alert.k_aus}</p>
                  <p>Latitude Band: ${alert.lat_band}</p>
                  <p>Description: ${alert.description}</p>
                `;
              } else {
                alertContainer.innerHTML = `<p>No active aurora alerts at this time.</p>`;
              }
            } catch (error) {
              console.error('Error fetching Aurora Alert data:', error);
              document.getElementById('aurora-alert-info').innerHTML = `<p>Error loading aurora alert data.</p>`;
            }
          }

          // Call the function when the page loads
          window.onload = fetchAuroraAlert;
        </script>
---