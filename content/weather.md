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
      title: Forecasts
      subtitle: This page displays various weather forecasts that I like having collated into one webpage.
      text: |
        <iframe src="https://free.timeanddate.com/clock/i9jtnvu4/tlau/fc111/bo2/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="123" height="48"></iframe><iframe src="https://free.timeanddate.com/clock/i9jtnvu4/tlau/fc111/bo2/pa6/tt0/tw1/tm3/td2/th1/ta1/tb4" frameborder="0" width="123" height="48"></iframe>
        {style="color: red"}

        <div style="width:1125px;">
          <div style="float:left;">
            <iframe width="560px" height="315px" src="https://www.youtube.com/embed/1ofKJZb-1eY" frameborder="0" allowfullscreen></iframe>
          </div>
          <div style="float:right;">
            <iframe width="560px" height="315px" src="https://www.youtube.com/embed/BJZm-BAg82g" frameborder="0" allowfullscreen></iframe>
          </div>
          <div style="clear:both;"></div>
        </div>

        <iframe width="650" height="650" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=mm&metricTemp=°C&metricWind=km/h&zoom=7&overlay=rain&product=ecmwf&level=surface&lat=-36.058&lon=149.26&detailLat=-35.251&detailLon=149.124&marker=true&message=true" frameborder="0"></iframe>

        <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=surface&lat=-35.514&lon=149.03" frameborder="0"></iframe>

        <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=100m&lat=-35.514&lon=149.03" frameborder="0"></iframe>

        <iframe width="300" height="300" src="https://embed.windy.com/embed.html?type=map&location=coordinates&metricRain=default&metricTemp=default&metricWind=default&zoom=7&overlay=wind&product=ecmwf&level=950h&lat=-35.514&lon=149.03" frameborder="0"></iframe>

        <div style="width: 650px;"><iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75234" width="650" height="520" frameborder="0"  scrolling="no"></iframe><a style="z-index: 1;position: relative;margin: -20px 0 0 0;text-indent: -9999em;display: block;height: 20px" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">Today's weather in OConnor</a></div>

        <div style="width: 300px;"><iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75235" width="300" height="520" frameborder="0"  scrolling="no"></iframe><a style="z-index: 1;position: relative;margin: -20px 0 0 0;text-indent: -9999em;display: block;height: 20px" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">Today's weather in OConnor</a></div>

        <div style="width: 400px;"><iframe style="display: block;" src="https://cdnres.willyweather.com.au/widget/loadView.html?id=75235" width="400" height="520" frameborder="0"  scrolling="no"></iframe><a style="display: block;text-indent: -9999em;position: relative;z-index: 1;height: 20px;margin: -20px 0 0 0" href="https://www.willyweather.com.au/act/canberra/oconnor.html" rel="nofollow">oconnor Forecast</a></div>

        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75236" type="application/javascript"></script>

        <script src="https://cdnres.willyweather.com.au/widget/warning/loadView.html?id=75237" type="application/javascript"></script>

        <small>Weather warnings are provided by BOM via <a href="https://www.willyweather.com.au">WillyWeather</a></small>
---