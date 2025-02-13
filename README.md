# WIP - project just started as a fork and it will _NOT_ work

## Heizoel24 meX Integration for Home Assistant

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

This custom integration adds support for the _meX_ WiFi
tank level sensor by Heizoel24.

It's based on a fork of [ecofrog](https://github.com/alexiosc/ecofrog)

<img alt="Photo of an EcoFrog sensor" src="https://d2j6dbq0eux0bg.cloudfront.net/images/34815086/1692822375.jpg" width="400" />

You get access to the information provided by the Heizoel24 API:

* Current volume of fluid in the tank
* Maximum volume of fluid in the tank
* Percentage of fluid
* Sensor temperature
* Battery (in volts)

## Installation

Since this is a custom component, you must copy the contents of the
`custom_components` folder/directory to your Home Assistant `config`
folder/directory, so it looks like this:

```
config/
└ custom_components/
  └ heizoel24-mex/ 
    ├ __init__.py
    └ ...
```

The exact method to do this depends on whether you're using a VM
image, HA appliance or Docker.

Once you've done this, restart Home Assistant, and the integration
should be visible. Go to Settings → Devices & Services, click the ADD
INTEGRATION button, then search for meX.

## Configuration

You need four pieces of information to authenticate with the
Heizoel24 API:

* a numeric user ID called a ‘username’,
* the E-Mail address you bought or registered the meX with,
* a ‘Security Stamp’, which is a UUID like `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`, and
* the Device ID, a numeric ID of the device to monitor.

Once you've added the device, it should appear in the Integrations,
and show one device for each of your meX, and several
sensors. These can be added to your dashboards or used in automations
as always.

## Multiple meX

If you have more than one meX, you need to add the integration
once for each sensor, using the appropriate authentication
information.

## Polling Frequency

In order to be nice to the API servers, polling is limited to once
every hour. A fresh copy of the data is fetched when Home Assistant
restarts.

The meX samples the tank a few times a day, but _seemingly_ only
uploads fresh data once per 24 hour period. So hourly polls should be
fine.

## Issues? Questions?

This is alpha software of the worst possible type.

I hope it works for you, and please let me know if it doesn't! I'd
especially like to know if it works correctly for multiple meX,
as I only have one.

