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

        <!-- weather warnings -->
        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75237" type="application/javascript"></script>
        <small>Weather warnings are provided by BOM via <a href="https://www.willyweather.com.au">WillyWeather</a></small>
---