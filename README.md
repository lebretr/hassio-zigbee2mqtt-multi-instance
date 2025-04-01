<div align="center">
    <a href="https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance">
        <img width="150" height="150" src="zigbee2mqtt/logo.png">
    </a>
    <br>
    <br>
    <div style="display: flex;">
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance/actions?query=workflow%3ACI_MI">
            <img src="https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance/workflows/CI_MI/badge.svg">
        </a>
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance/releases">
            <img src="https://img.shields.io/github/release/lebretr/hassio-zigbee2mqtt-multi-intance.svg">
        </a>
        <a href="https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance/stargazers">
            <img src="https://img.shields.io/github/stars/lebretr/hassio-zigbee2mqtt-multi-intance.svg">
        </a>
        <a href="https://discord.gg/dadfWYE">
            <img src="https://img.shields.io/discord/556563650429583360.svg">
        </a>
    </div>
    <h1>Zigbee2MQTT Multi-Instance Home Assistant add-on based on the Official Zigbee2MQTT add-on </h1>
</div>

> [!CAUTION]
> If you're using a Raspberry Pi, ensure you have at least a Raspberry Pi 4, as running it on a Raspberry Pi 3 may cause instability due to its limited resources.

## IMPORTANT
This repositiry is a fork of `https://github.com/zigbee2mqtt/hassio-zigbee2mqtt`

The only difference with the official `zigbee2mqtt/hassio-zigbee2mqtt` is that you can deploy several instances of zigbee2mqtt when you want use several zigbee adapters with your home assistant

My work was only to duplicate the `zigbee2mqtt` directory and change some values in the config file in each duplicated directory.

## Installation

1. If you don't have an MQTT broker yet; in Home Assistant go to **[Settings → Add-ons → Add-on store](https://my.home-assistant.io/redirect/supervisor_store/)** and install the **[Mosquitto broker](https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mosquitto)** add-on, then start it.
1. Go back to the **Add-on store**, click **⋮ → Repositories**, fill in</br> `https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance` and click **Add → Close** or click the **Add repository** button below, click **Add → Close** (You might need to enter the **internal IP address** of your Home Assistant instance first).  
   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Flebretr%2Fhassio-zigbee2mqtt-multi-intance)
1. The repository includes:
   - **Zigbee2MQTT** is the official stable release that tracks the released versions of Zigbee2MQTT. (**recommended for most users**)
   - **Zigbee2MQTT Edge** tracks the `dev` branch of Zigbee2MQTT such that you can install the edge version if there are features or fixes in the Zigbee2MQTT dev branch that are not yet released.
1. Click on the add-on and press **Install** and wait till the add-on is installed.
1. Start the add-on by going to **Info** and click **Start**
1. Wait a few seconds and press **OPEN WEB UI**, you will now see the onboarding page. More information about the onboarding can be found [here](https://www.zigbee2mqtt.io/guide/getting-started/#onboarding).
1. Fill in the desired settings, for most setups changing the following is enough:
   - Select your adapter under _Found Devices_, this will configure the _Coordinator/Adapter Port/Path_ and _Coordinator/Adapter Type/Stack/Driver_.
   - Fill in the _Closests WiFi Channel_ to select the most optimal Zigbee channel.
1. Press **Submit**, Zigbee2MQTT will now start, wait a few seconds and refresh the page. You should now see the Zigbee2MQTT frontend.
   - If it shows `502: Bad Gateway` wait a bit more and refresh the page.
   - If this takes too long (e.g. 2 minutes +) check the **Log** tab to see what went wrong.
   - In case the add-on fails to start with the following error: `USB adapter discovery error (No valid USB adapter found). Specify valid 'adapter' and 'port' in your configuration.`, we need to fill in the `serial` section. Format can be found [here](https://www.zigbee2mqtt.io/guide/configuration/adapter-settings.html#adapter-settings), but skip the initial `serial:` indent. e.g.: <br>
     ```yaml
     adapter: zstack
     port: /dev/serial/by-id/usb-Texas_Instruments_TI_CC2531_USB_CDC___0X00124B0018ED3DDF-if00
     ```
     If you don't know the port and you have just one USB device connected to your machine try `/dev/ttyUSB0` or `/dev/ttyAMA0`. Else use the [Home Assistant CLI](https://www.home-assistant.io/common-tasks/os#home-assistant-via-the-command-line) and execute `ha hardware info` to find out.

For configuration, refer to [the documentation of the official add-on](https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)
