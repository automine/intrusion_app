# Intrusion App for Splunk

## Overview
Many organizations is IDS/IPS devices and software as their first line of defense against attackers. This app provides Splunk dashboards, forms, and reports which can be used to explore your IDS events across your different sourcetypes.

To do this, the app relies on the Splunk Common Information Model (CIM) for IDS attack events. This means that the app can report on any authentication data, as long as it has been on-boarded properly, and is available through the [Intrusion Detection data model](http://docs.splunk.com/Documentation/CIM/latest/User/IntrusionDetection), including network, host, wireless, and application products.

## A note on Splunk Data Model Acceleration and Disk Space
This app requires data model acceleration, which will use additional disk space. If you are using the Splunk App for Enterprise Security, this is already enabled, and should have been factored into your retention policies. If not, you should review the documentation on [data model acceleration, how it uses disk space, and how to plan for it](http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Acceleratedatamodels#Data_model_summary_size_on_disk).

## A note on the Splunk Common Information Model
As mentioned above, the app uses the CIM for authentication events. The CIM allows you to take events from a number of sources or products, and report on them in one cohesive manner, using a common set of names for fields and event types.

## Available Dashboards

### Intrusion Overview
Provides a starting point for exploring your IDS events. Most panels will drill-down to other pages in the application.

### Attack Source Profile
A view based on the source of IDS events.

### Attack Destination Profile
IDS events where attacks are launched against the same destination.

### Attack Signature Profile
Panels which focus on events which all are from the same identified with the same signature.

### Attack Category Profile
A view focusing on attacks which fall into the same category (as defined in the events).

### Attack Search
A form for finding events based on various field values.

### Sourcetypes (Advanced)
Information about the sourcetypes which are present in the accelerated data.

## Prerequisites

### Splunk Versions
This app has been tested with Splunk versions 6.6. This app should be installed on the same search head on which the Authentication data model has been accelerated.

### Splunk Common Information Model Add-on
This app depends on data models included in the Splunk Common Information Model Add-on, specifically the "Authentication" data model. Please review the information on [installing and using the Splunk Common Information Model Add-on](http://docs.splunk.com/Documentation/CIM/latest/User/Install) and information on [configuring the acceleration on the data model](http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Acceleratedatamodels#Enable_persistent_acceleration_for_a_data_model).

The Splunk Common Information Model Add-on can be downloaded from [Splunkbase](https://apps.splunk.com/app/1621/).

This app has been tested with versions 4.9 of the CIM add-on. 

### Data model Acceleration on the Intrusion data model
In order to make the app respond and load quickly, accelerated data models are used to provide summary data. For this data to be available, the `Intrusion Detection` data model must be accelerated. Information on how to enable acceleration for the `Intrusion Detection` data model can be found [here](http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Managedatamodels#Enable_data_model_acceleration). The data model must be accelerated for the length of time for which you would like to see reporting.

## Installation
This app should be installed on a search head where the `Intrusion Detection` data model has been accelerated. More information on installing or upgrading Splunk apps can be found [here](http://docs.splunk.com/Documentation/Splunk/latest/Admin/Wheretogetmoreapps).

### Simple Installation Process
1. Make sure the field extractions and tags on your authentication events are correct.
2. Install the Splunk Common Information Model Add-on (skip if you are installing on an ES search head).
4. Install the Intrusion App for Splunk.
5. Enable accelerations on the `Intrusion Detection` data model (skip if you are installing on an ES search head).
6. Wait for the accelerations to start. After the acceleration searches have run, you should start seeing the dashboards populate.

## About support for this app
Support for this app is provided on a best-effort basis. We have released this app for free, and want to help solve issues, and add features, but we also have day-jobs. The Github repo to report issues can be found [here](https://github.com/automine/intrusion_app).

Need help? Use the Splunk community resources! I can be found on many of them:

* [Splunk Answers](https://answers.splunk.com/)
* [#splunk on Efnet IRC](https://wiki.splunk.com/Community:IRC)
* [Splunk Slack channel](http://splunk402.com/chat/)

## References

### Splunk Common Information Model
* [Splunk Common Information Model Add-on Docs](http://docs.splunk.com/Documentation/CIM/latest/User/Overview)
* [Splunk Common Information Model add-on Authentication data model](http://http://docs.splunk.com/documentation/cim/latest/user/Authentication)

### Downloads
* Splunk Common Information Model Add-on Download: <https://apps.splunk.com/app/1621/>

## Credits
This app was created by David Shpritz of [Aplura, LLC.](http://www.aplura.com/)

## Release history

### v1.1
Removed stray stanza in app.conf

### v1.0
Initial release
