# UPDATE NOTICE

This is now deprecated in favor of [envisalink_new](https://github.com/ufodone/envisalink_new) which will eventually be merged back into Home Assistant.

If you are using this integration, please consider switching to `envisalink_new`.  Thanks!


# Temporary Home Assistant Envisalink Clone for DSC Alarm Systems
A HACS integration which is a clone of the Envisalink integration with the zone bypass switches enabled.

Because the zone bypass switch feature does not currently work for DSC alarm panels which require the alarm code to bypass a zone, there is a need to add a configuration option to enable/disable the feature.  Home Assistant is no longer accepting PRs which add new configuration options for integrations that do not use config flow for their configuration.  As a result, I need to first get the Envisalink integration updates to use config flow which I'm both unfamiliar with and have not been able to find the time to do yet.

This HACS integration is meant only as a temporary solution for anyone wishing to use the zone bypass switches until I can find time to get the official Envisalink integration upgraded to use config flow for its configuration and, in turn, the zone bypass switch feature back into the official version.

## WARNING ##
The integration only works DSC alarm panels and only if the panel is configure such that zone bypass does **NOT** require an alarm code.  If you use this integration with a panel that requires an alarm code for zone bypass, it can result in your physical panel becoming unresponsive and in some cases may even trigger your alarm.  **Proceed with caution!**

## Configuration
To avoid conflicts with the official integration, this one has been renamed to "dscalarm".  This means that you will need to change your `configuration.yaml` to use `dscalarm` instead of `envisalink`.  The devices and entities will still be created with the same names so anything referencing them should not be affected.

For example:

```
envisalink:
  host: "hostname"
  panel_type: "DSC"
  ...
```

would change to:

```
dscalarm:
  host:"hostname"
  panel_type: "DSC"
  ...
```

Zone bypass switches are disabled by default.  To enable them, add the following to your config:

```
  create_zone_bypass_switches: true
```
