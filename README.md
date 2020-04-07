## Collects and decodes the result logs written by osqueryd in the JSON format.

To set up osqueryd follow the osquery installation instructions for your operating system and configure the ```filesystem``` logging driver (the default). Make sure UTC timestamps are enabled.

When you run this module, it performs a few tasks under the hood:

- Sets the default paths to the log files (but don’t worry, you can override the defaults)
- Makes sure each multiline log event gets sent as a single event
- Uses ingest node to parse and process the log lines, shaping the data into a structure suitable for visualizing in Kibana
- Deploys dashboards for visualizing the log data

### Compatibility

The ```Osquery``` module was tested with logs from osquery version 2.10.2. Since the results are written in the JSON format, it is likely that this module works with any version of osquery.

This module is available on Linux, macOS, and Windows.

## Installation

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

### Windows:

<i>If you haven't already installed filebeat...</i>

1) As administrator, enter the following command in Powershell or download the zip file [here](https://github.com/themarcusaurelius/Filebeat-Modules/archive/master.zip).

```
Start-BitsTransfer -Source 'https://github.com/themarcusaurelius/Filebeat-Modules/archive/master.zip' -Destination 'C:\Users\Administrator\Downloads\Filebeat-Modules.zip'
```

2) Unzip the package and extract the contents to the `C:/` drive.

3) Back in Powershell, CD into the extracted folder and run the following script:

```
.\installFilebeat.ps1
```

4) When prompted, enter your credentials below and click OK.

```css
Kibana URL: _PLACEHOLDER_KIBANA_URL_
Username: _PLACEHOLDER_USERNAME_
Password: _PLACEHOLDER_PASSWORD_
Elasticsearch API Endpoint: _PLACEHOLDER_API_ENDPOINT_
```

5) Choose the ```Osquery``` module and click OK.

This will install and run Filebeat with the module you enabled set to that particular modules default file path.

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

<br>


<i>If you have already installed filebeat...</i>

1) In Powershell, as administrator, CD into the ```Filebeat``` folder and enter the following command:

```
.\filebeat.exe modules enable osquery
```

2) Restart Filebeat to initate the changes.

```
restart-service filebeat
```

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

<hr>

## Example Dashboard

This module comes with a sample dashboard for visualizing the data collected by the "compliance" pack. To collect this data, enable the ```id-compliance``` pack in the osquery configuration file.

![Imgur](https://imgur.com/Ucf357R.png)
