## Collects and decodes the result logs written by osqueryd in the JSON format.

To set up osqueryd follow the osquery installation instructions for your operating system and configure the ```filesystem``` logging driver (the default). Make sure UTC timestamps are enabled.

When you run this module, it performs a few tasks under the hood:

- Sets the default paths to the log files (but don’t worry, you can override the defaults)
- Makes sure each multiline log event gets sent as a single event
- Uses ingest node to parse and process the log lines, shaping the data into a structure suitable for visualizing in Kibana
- Deploys dashboards for visualizing the log data

### Compatibility

The ```osquery``` module was tested with logs from osquery version 2.10.2. Since the results are written in the JSON format, it is likely that this module works with any version of osquery.

This module is available on Linux, macOS, and Windows.

### Installation

### Linux:

<i>If you haven't already installed filebeat...</i>

1. Enter the following script into the console using elevated privileges

```
curl https://github.com/themarcusaurelius/vizion.ai/blob/master/beat-install-scripts/install-config-osquery.sh > install-config-osquery.sh; chmod a+x  install-config-osquery.sh; ./install-config-osquery.sh _PLACEHOLDER_API_ENDPOINT_
```

2. When prompted, select the proper environment to complete the installation.

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

<i>If you have already installed filebeat...</i>

1. Enable the module.

```
filebeat modules enable osquery 
```

2. Restart Filebeat.

```
service filebeat restart
```

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

<hr>

## Example Dashboard

This module comes with a sample dashboard for visualizing the data collected by the "compliance" pack. To collect this data, enable the ```id-compliance``` pack in the osquery configuration file.

![Imgur](https://imgur.com/Ucf357R.png)
