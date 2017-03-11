SorjaCon LTD (GlucoScan)
======================================

This acts as a web-based CGM (Continuous Glucose Monitor) to allow
multiple caregivers to remotely view a patient's glucose data in
real time.  The server reads a MongoDB which is intended to be data
from a physical CGM, where it sends new SGV (sensor glucose values) as
the data becomes available.  The data is then displayed graphically
and blood glucose values are predicted 0.5 hours ahead using an
autoregressive second order model.  Alarms are generated for high and
low values, which can be cleared by any watcher of the data.

# [#WeAreNotWaiting](https://twitter.com/hashtag/wearenotwaiting?src=hash&vertical=default&f=images) and [this](https://vimeo.com/109767890) is why.


[build-img]: https://img.shields.io/travis/nightscout/cgm-remote-monitor.svg
[build-url]: https://travis-ci.org/nightscout/cgm-remote-monitor
[dependency-img]: https://img.shields.io/david/nightscout/cgm-remote-monitor.svg
[dependency-url]: https://david-dm.org/nightscout/cgm-remote-monitor
[coverage-img]: https://img.shields.io/coveralls/nightscout/cgm-remote-monitor/dev.svg
[coverage-url]: https://coveralls.io/github/nightscout/cgm-remote-monitor?branch=dev
[codacy-img]: https://www.codacy.com/project/badge/f79327216860472dad9afda07de39d3b
[codacy-url]: https://www.codacy.com/app/Nightscout/cgm-remote-monitor
[gitter-img]: https://img.shields.io/badge/Gitter-Join%20Chat%20%E2%86%92-1dce73.svg
[gitter-url]: https://gitter.im/nightscout/public
[heroku-img]: https://www.herokucdn.com/deploy/button.png
[heroku-url]: https://heroku.com/deploy
[original]: https://github.com/rnpenguin/cgm-remote-monitor

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**
    - [Alarms](#alarms)
    - [Core](#core)
    - [Plugins](#plugins)
      - [Default Plugins](#default-plugins)
      - [Advanced Plugins](#advanced-plugins)
      - [Extended Settings](#extended-settings)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Alarms

  These alarm setting effect all delivery methods (browser, pushover, maker, etc), some settings can be overridden per client (web browser)

  * `BG_HIGH` (`260`) - must be set using mg/dl units; the high BG outside the target range that is considered urgent
  * `BG_LOW` (`55`) - must be set using mg/dl units; the low BG outside the target range that is considered urgent
  * `ALARM_URGENT_HIGH` (`on`) - possible values `on` or `off`
  * `ALARM_HIGH` (`on`) - possible values `on` or `off`
  * `ALARM_LOW` (`on`) - possible values `on` or `off`
  * `ALARM_URGENT_LOW` (`on`) - possible values `on` or `off`
  
# Core

  * `MONGO_COLLECTION` (`entries`) - The collection used to store SGV, MBG, and CAL records from your CGM device
  * `MONGO_TREATMENTS_COLLECTION` (`treatments`) -The collection used to store treatments entered in the Care Portal, see the `ENABLE` env var above
  * `MONGO_DEVICESTATUS_COLLECTION`(`devicestatus`) - The collection used to store device status information such as uploader battery
  * `MONGO_PROFILE_COLLECTION`(`profile`) - The collection used to store your profiles
  * `MONGO_FOOD_COLLECTION`(`food`) - The collection used to store your food database


  
  
# Plugins

  Plugins are used extend the way information is displayed, how notifications are sent, alarms are triggered, and more.

  The built-in/example plugins that are available by default are listed below.  The plugins may still need to be enabled by adding to the `ENABLE` environment variable.

## Default Plugins

  These can be disabled by setting the `DISABLE` env var, for example `DISABLE="direction upbat"`

## Extended Settings
  Some plugins support additional configuration using extra environment variables.  These are prefixed with the name of the plugin and a `_`.  For example setting `MYPLUGIN_EXAMPLE_VALUE=1234` would make `extendedSettings.exampleValue` available to the `MYPLUGIN` plugin.

  Plugins only have access to their own extended settings, all the extended settings of client plugins will be sent to the browser.

  
License
---------------

[agpl-3]: http://www.gnu.org/licenses/agpl-3.0.txt

    cgm-remote-monitor - web app to broadcast cgm readings
    Copyright (C) 2015 The Nightscout Foundation, http://www.nightscoutfoundation.org.

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as published
    by the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

 
