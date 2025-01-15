---
title: Qbus
description: Instructions on how to integrate your Qbus installation with Home Assistant.
ha_category:
  - Switch
ha_platforms:
  - switch
ha_iot_class: Local Push
ha_codeowners:
  - '@Qbus-iot'
  - '@thomasddn'
ha_release: 2024.12
ha_domain: qbus
ha_integration_type: device
ha_config_flow: true
---

The **Qbus** {% term integration %} allows you to integrate your [Qbus Control](https://www.qbus.be) into Home Assistant. **Qbus** is a Belgian manufacturer of Home Automation systems.

## Prerequisites

This integration communicates with a **Qbus** controller over an MQTT server.

The controllers cannot communicate directly with MQTT. Therefore, you need to install the Qbus gateway before enabling this integration. The Qbus gateway is a software tool that runs on all Linux platforms. It can be installed by running a script or a Docker container. For detailed instructions, please refer to the [Qbus MQTT Gateway documentation](https://github.com/Qbus-iot/qbus-mqttgw).

We also host a site which contains a [Manual](https://iot.qbus.be/) where you can find lots of information to set up Home Assistant with a **Qbus** controller (currently only available in Dutch, with translations planned for the future).

When you have your controller connected to the MQTT Server, you need to set up an MQTT client in Home Assistant to enable communication between Home Assistant and your **Qbus** system. This client should connect to the same MQTT Server as your Qbus controller. For detailed instructions, refer to the [MQTT integration documentation](https://www.home-assistant.io/integrations/mqtt/).

{% include integrations/config_flow.md %}

## Supported devices

There is currently support for the following **Qbus** products within Home Assistant:

- **CTD 3.0**: main controller.
- **CTD 3.5**: main controller.

## Available entities

- **Switch**: toggles Bistable outputs on relay modules.

## Removing the integration

This integration follows standard integration removal. No extra steps are required.

{% include integrations/remove_device_service.md %}

## Data updates

All data from **Qbus** entities are pushed to Home Assistant over MQTT.

## Known limitations

The integration does not provide a way to update the firmware on the devices. This can only be done with the configuration software System Manager.

## Troubleshooting

### Can’t set up the device

#### Symptom: "No devices are discovered"

When trying to set up the integration, no devices are discovered.

##### Description

This means that the integration did not receive a valid configuration from the gateway.

##### Resolution

To resolve this issue, try the following steps:

1. Make sure your controller is online and not connected to System Manager.
2. Make sure you have an MQTT broker running.
3. Make sure that the gateway software is up and running (see Prerequisites) and connected to the broker.
4. Make sure you have an MQTT client integration (see Prerequisites) connected to the broker.
