<div align="center">
    <a href="https://github.com/lebretr/hassio-zigbee2mqtt-mi">
        <img width="150" height="150" src="zigbee2mqtt/logo.png">
    </a>
    <br>
    <br>
    <div style="display: flex;">
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-mi/actions?query=workflow%3ACI_MI">
            <img src="https://github.com/lebretr/hassio-zigbee2mqtt-mi/workflows/CI_MI/badge.svg">
        </a>
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-mi/releases">
            <img src="https://img.shields.io/github/release/lebretr/hassio-zigbee2mqtt-mi.svg">
        </a>
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-mi/stargazers">
            <img src="https://img.shields.io/github/stars/lebretr/hassio-zigbee2mqtt-mi.svg">
        </a>
    </div>
    <h1>Zigbee2MQTT Multi-Instance Home Assistant add-on base on the Official Zigbee2MQTT add-on </h1>
</div>


## IMPORTANT
This repositiry is a fork of `https://github.com/zigbee2mqtt/hassio-zigbee2mqtt`

The only difference with the official `zigbee2mqtt/hassio-zigbee2mqtt` is that you can deploy several instances of zigbee2mqtt when you want use several zigbee adapter with your home assistant

My work was only to duplicate the `zigbee2mqtt` directory and change some values in the config file in each duplicated directory.

## Installation

1. If you don't have an MQTT broker yet; in Home Assistant go to **[Settings → Add-ons → Add-on store](https://my.home-assistant.io/redirect/supervisor_store/)** and install the **[Mosquitto broker](https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mosquitto)** add-on, then start it.
1. Go back to the **Add-on store**, click **⋮ → Repositories**, fill in</br> `https://github.com/lebretr/hassio-zigbee2mqtt-mi` and click **Add → Close** or click the **Add repository** button below, click **Add → Close** (You might need to enter the **internal IP address** of your Home Assistant instance first).  
   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Flebretr%2Fhassio-zigbee2mqtt-mi)
1. The repository includes:
   - **Zigbee2MQTT** is the official stable release that tracks the released versions of Zigbee2MQTT. (**recommended for most users**)
   - **Zigbee2MQTT Edge** tracks the `dev` branch of Zigbee2MQTT such that you can install the edge version if there are features or fixes in the Zigbee2MQTT dev branch that are not yet released.
   - **Zigbee2MQTT Multi-instance N°x** is a duplicated stable release that tracks the released versions of Zigbee2MQTT. Use this if you want to use a second (or more) zigbee coordinator adaptater

For configuration, refer to [the documentation of the official add-on](https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)
