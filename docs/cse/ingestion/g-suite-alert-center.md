---
id: g-suite-alert-center
title: G Suite Alert Center
sidebar_label: G Suite Alert Center
description: Collect log messages from G Suite Alert Center to be parsed by CSE's system parser for G Suite Alert Center.
---

## Step 1: Configure collection

In this step, you configure an HTTP Source to collect G Suite Alert Center log messages. You can configure the source on an existing Hosted Collector or create a new collector. If you’re going to use an existing collector, jump to [Configure an HTTP Source below.](#configure-an-http-source) Otherwise, create a new collector as described in [Configure a hosted collector](#configure-a-hosted-collector) below, and then create the HTTP Source on the collector.

### Configure a Hosted Collector

1. In the Sumo Logic platform, select **Manage Data \> Collection \> Collection**.
1. Click **Add Collector**.
1. Click **Hosted Collector.**
1. The **Add Hosted Collector** popup appears.  
    ![add-hosted-collector.png](/img/cse/add-hosted-collector.png)
1. **Name**. Provide a Name for the Collector.
1. **Description**. (Optional)
1. **Category**. Enter a string to tag the output collected from the source. The string that you supply will be saved in a metadata field called `_sourceCategory`. 
1. **Fields**. 
    1. If you are planning that all the sources you add to this collector will forward log messages to CSE, click the **+Add Field** link, and add a field whose name is `_siemForward` and value is *true*. This will cause the collector to forward all of the logs collected by all of the sources on the collector to CSE.
    1. If all sources in this collector will be G Suite Alert Center, add an additional field with key `_parser` and value */Parsers/System/Google/G Suite Alert Center*.

:::note
It’s also possible to configure individual sources to forward to CSE, as described in the following section.
:::

### Configure an HTTP Source

1. In Sumo Logic, select **Manage Data \> Collection \> Collection**. 
1. Navigate to the Hosted Collector where you want to create the source.
1. On the **Collectors** page, click **Add Source** next to a Hosted Collector.
1. Select **HTTP Logs & Metrics**. 
1. The page refreshes.  
    ![http-source.png](/img/cse/http-source.png)
1. **Name**. Enter a name for the source. 
1. **Description**. (Optional) 
1. **Source Host.** (Optional) Enter a string to tag the messages collected from the source. The string that you supply will be saved in a metadata field called `_sourceHost.`
1. **Source Category**. Enter a string to tag the output collected from the source. The string that you supply will be saved in a metadata field called `_sourceCategory`.
1. **Fields.** If you are not parsing all sources in the hosted collector with the same parser, click the **+Add Field** link, and add a field whose name is `_parser` with value */Parsers/System/Google/G Suite Alert Center*.
1. **Advanced Options for Logs**. Under **Timestamp Format**, select **Specify a format.**
    1. **Format**. Enter `yyyy-MM-dd'T'HH:mm:ss.SSS'Z'`
    1. **Timestamp locator**. Enter `\"createTime\":(.*),`
    1. Click **Add.**
1. Click **Save**.
1. Make a note of the HTTP Source URL that is displayed. You’ll supply it in [Step 2](#step-2-configure-g-suite-alert-center) below.

## Step 2: Configure G Suite Alert Center

In this step you configure G Suite Alert Center to send logs to Sumo Logic. You can configure a G Suite Alert Center collector in Google Cloud Platform (GCP), or via a script on a Linux machine. Choose the method that is best suited for you:

* Google Cloud Platform (GCP) collection
* Script-based collection

## Step 3: Verify ingestion

1. In this step, you verify that your logs are successfully making it into CSE. 
1. Click the gear icon, and select **Log Mappings** under **Incoming Data**.  
    ![log-mappings-link.png](/img/cse/log-mappings-link.png)
1. On the Log Mappings page search for "G Suite Alert Center" and check under **Record Volume**.  
    ![gsuite-record-volume.png](/img/cse/gsuite-record-volume.png)
1. For a more granular look at the incoming records, you can also search the Sumo Logic platform for G Suite Alert Center security records.  
    ![gsuite-search.png](/img/cse/gsuite-search.png)
