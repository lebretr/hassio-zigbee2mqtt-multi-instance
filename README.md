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
    </div>
    <h1>Zigbee2MQTT Multi-Instance Home Assistant add-on based on the Official Zigbee2MQTT add-on </h1>
</div>


1. If you don't have an MQTT broker yet; in Home Assistant go to **[Settings → Add-ons → Add-on store](https://my.home-assistant.io/redirect/supervisor_store/)** and install the **[Mosquitto broker](https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mosquitto)** add-on, then start it.
1. Go back to the **Add-on store**, click **⋮ → Repositories**, fill in</br> `https://github.com/zigbee2mqtt/hassio-zigbee2mqtt` and click **Add → Close** or click the **Add repository** button below, click **Add → Close** (You might need to enter the **internal IP address** of your Home Assistant instance first).  
   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fzigbee2mqtt%2Fhassio-zigbee2mqtt)
1. The repository includes two add-ons:
   - **Zigbee2MQTT** is the stable release that tracks the released versions of Zigbee2MQTT. (**recommended for most users**)
   - **Zigbee2MQTT Edge** tracks the `dev` branch of Zigbee2MQTT such that you can install the edge version if there are features or fixes in the Zigbee2MQTT dev branch that are not yet released.
1. Click on the add-on and press **Install** and wait till the add-on is installed.
1. Click on **Configuration**
   - If you are **not** using the Mosquitto broker add-on fill in your MQTT details (leave empty when using the Mosquitto broker add-on) under the `mqtt` section. Format can be found [here](https://www.zigbee2mqtt.io/guide/configuration/mqtt.html#server-connection), but skip the initial `mqtt:` indent. e.g.: <br>
     ```yaml
     server: mqtt://localhost:1883
     user: my_user
     password: "my_password"
     ```
     Note: If the `password` includes certain special characters (reserved by yaml specification), the enclosing quotes are required. So it is recommended to always quote it when in doubt.
   - Since Zigbee2MQTT automatically attempts to detect the adapter, you can leave the `serial` section empty for now; we may need it later in step 7.
   - Click **Save**
   - **Tip:** it is possible to refer to variables in the Home Assistant `secrets.yaml` file (not the Zigbee2MQTT one!) by using e.g. `password: '!secret mqtt_pass'`
   - **CAUTION:** settings configured through the add-on configuration page will take precedence over settings in the `configuration.yaml` page (e.g. you set `rtscts: false` in add-on configuration page and `rtscts: true` in `configuration.yaml`, `rtscts: false` will be used).
1. Start the add-on by going to **Info** and click **Start**
1. Wait till Zigbee2MQTT starts and press **OPEN WEB UI** to verify Zigbee2MQTT started correctly.
   - If it shows `502: Bad Gateway` wait a bit more and refresh the page.
   - If this takes too long (e.g. 2 minutes +) check the **Log** tab to see what went wrong.
   - In case the add-on fails to start with the following error: `USB adapter discovery error (No valid USB adapter found). Specify valid 'adapter' and 'port' in your configuration.`, we need to fill in the `serial` section (which we skipped in step 5). Format can be found [here](https://www.zigbee2mqtt.io/guide/configuration/adapter-settings.html#adapter-settings), but skip the initial `serial:` indent. e.g.: <br>
     ```yaml
     adapter: zstack
     port: /dev/serial/by-id/usb-Texas_Instruments_TI_CC2531_USB_CDC___0X00124B0018ED3DDF-if00
     ```
     If you don't know the port and you have just one USB device connected to your machine try `/dev/ttyUSB0` or `/dev/ttyAMA0`. Else use the [Home Assistant CLI](https://www.home-assistant.io/common-tasks/os#home-assistant-via-the-command-line) and execute `ha hardware info` to find out.

The only difference with the official `zigbee2mqtt/hassio-zigbee2mqtt` is that you can deploy several instances of zigbee2mqtt when you want use several zigbee adapters with your home assistant

My work was only to duplicate the `zigbee2mqtt` directory and change some values in the config file in each duplicated directory.

## Installation

1. If you don't have an MQTT broker yet; in Home Assistant go to **[Settings → Add-ons → Add-on store](https://my.home-assistant.io/redirect/supervisor_store/)** and install the **[Mosquitto broker](https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mosquitto)** add-on, then start it.
1. Go back to the **Add-on store**, click **⋮ → Repositories**, fill in</br> `https://github.com/lebretr/hassio-zigbee2mqtt-multi-intance` and click **Add → Close** or click the **Add repository** button below, click **Add → Close** (You might need to enter the **internal IP address** of your Home Assistant instance first).  
   [![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Flebretr%2Fhassio-zigbee2mqtt-multi-intance)
1. The repository includes:
   - **Zigbee2MQTT** is the official stable release that tracks the released versions of Zigbee2MQTT. (**recommended for most users**)
   - **Zigbee2MQTT Edge** tracks the `dev` branch of Zigbee2MQTT such that you can install the edge version if there are features or fixes in the Zigbee2MQTT dev branch that are not yet released.
   - **Zigbee2MQTT Multi-instance N°x** is a duplicated stable release that tracks the released versions of Zigbee2MQTT. Use this if you want to use a second (or more) zigbee coordinator adaptater

For configuration, refer to [the documentation of the official add-on](https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)
