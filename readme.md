## Rundeck Job Activity Template

This InfluxDB Template can be used to monitor ithe execution activity of your Rundeck jobs.

![Rundeck Execution Dashboard Screenshot](img/RundeckScreen.png)

### Quick Install

#### InfluxDB UI

In the InfluxDB UI, go to Settings->Templates and enter this URL: https://raw.githubusercontent.com/chobbs/local-templates/master/rundeck/rundeck.yml

#### Influx CLI
If you have your InfluxDB credentials [configured in the CLI](https://v2.docs.influxdata.com/v2.0/reference/cli/influx/config/), you can install this template with:

```
influx apply -u https://raw.githubusercontent.com/chobbs/local-templates/master/rundeck/rundeck.yml
```

### Included Resources

- 1 Bucket: `rundeck`, 7d retention
- Labels: `rundeck` + Telegraf Plugin Labels
- 1 Telegraf Configuration
- 1 Dashboard: `Rundeck Execution Activit`

## Setup Instructions

  General instructions on using InfluxDB Templates can be found in the [use a template](../docs/use_a_template.md) document.
    
  The data for the dashboard is populated by the included Telegraf configuration. The Telegraf Configuration requires the following environment variables
    
  - `INFLUX_TOKEN` - The token with the permissions to read Telegraf configs and write data to the `telegraf` bucket. You can just use your operator token to get started.
  - `INFLUX_ORG` - The name of your Organization (this will be your email address on the InfluxDB Cloud free tier)
  - `INFLUX_HOST` - The URL of your InfluxDB host (this can your localhost, a remote instance, or InfluxDB Cloud)

  You **MUST** set these environment variables before running Telegraf using something similar to the following commands
    
  - This can be found on the `Load Data` > `Tokens` page in your browser: `export INFLUX_TOKEN=TOKEN`
  - Your Organization name can be found on the Settings page in your browser: `export INFLUX_ORG=my_org`

## Running Telegraf

  To get resource data from your Linux hosts, [download and install Telegraf](https://portal.influxdata.com/downloads/) on those hosts. InfluxData provides native packages for a number of distributions as well as binaries that can be executed directly.

  Start Telegraf using the instructions from the `Load Data` > `Telegraf` > `Setup Instructions` link in the UI.

## Customizations

You can run the provided Telegraf configuration on multiple Linux machines, and switch between them using the `linux_host` filter at the top of the dashboard.

## Contact

Provide a way for users to get in touch with you if they have questions or need help using your template. What information you give is up to you, but we encourage providing those below.

- Author: Craig Hobbs
- Email: chobbs@pagerduty.comm
- Github: [@chobbs](https://github.com/chobbs)
