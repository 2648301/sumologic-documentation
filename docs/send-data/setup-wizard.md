---
id: setup-wizard
title: Sumo Logic Setup Wizard
sidebar_label: Setup Wizard
description: Use the Setup Wizard to quickly get started sending data to Sumo Logic.
---

import useBaseUrl from '@docusaurus/useBaseUrl';

The Setup Wizard lets you get data in your Sumo Logic account quickly. It guides you step-by-step based on the type of data you want to send. After data collection is running, the Setup Wizard installs a Sumo Logic App with pre-configured Dashboards that allow you to analyze your data. The Setup Wizard provides detailed instructions to help you with each step of the configuration.

Before you begin, [sign up](https://help.sumologic.com/01Start-Here/04Getting-Started/01-How-to-Sign-Up-for-Sumo-Logic) for a Sumo Logic account and activate it.

To open the Setup Wizard, select **Manage Data > Collection > Collection** and click the **Setup Wizard** link on the top right of the Collection page.

<img src={useBaseUrl('img/get-started/setup-wizard.png')} alt="setup-wizard" />

:::note
Keyboard shortcuts are not available when the Setup Wizard is open.
:::

## Upload log files

A great way to try out Sumo Logic for the first time is to upload a local log file. To do this, click **Upload Log Files**. You can upload up to 20 files and 100MB total per upload.

Uploading a local file allows you to try Sumo Logic without configuring a Collector to ingest live, streaming data. To continuously monitor a file in your environment, [configure a Collector and Source](https://help.sumologic.com/03Send-Data/01-Design-Your-Deployment) within Sumo Logic.

The following file types are **not** supported:

* bz2
* dmg
* doc
* docx
* exe
* gif
* jpg
* jpeg
* pdf
* png
* ppt
* pptx
* svg
* tar
* tgz
* xls
* xlsx
* zip


## Troubleshoot Setup Wizard issues

If you are having trouble installing a Collector and configuring a Source using the Setup Wizard, check the following issues.


### "Waiting for the Collector Installation" Message and Spinner

If you see the message "Waiting for the Collector Installation", the spinner never resolves, and the **Continue **button never becomes active, a previously installed Collector may be preventing the new installation.

You will need to uninstall the old Collector manually, then try to install a new Collector again. Steps on installing and uninstalling based on the operating system the Collector is run on can be found in the following links,

* [Linux](https://help.sumologic.com/03Send-Data/Installed-Collectors/04Install-a-Collector-on-Linux)
* [macOS](https://help.sumologic.com/03Send-Data/Installed-Collectors/02Install-a-Collector-on-MacOS)
* [Windows](https://help.sumologic.com/03Send-Data/Installed-Collectors/03Install-a-Collector-on-Windows)


### "It looks like you haven't activated your account..."

When you sign up for a Sumo Logic Trial account, the system automatically sends you an [activation email](https://help.sumologic.com/01Start-Here/04Getting-Started/01-How-to-Sign-Up-for-Sumo-Logic). To activate your new account, go to your email, click the **Activate Now** link, then complete and submit the activation form. When you complete this process, the Setup Wizard is displayed in a _new_ tab.

But if you return to the Setup Wizard in your _original_ tab, you may see a blocking overlay that displays the message **“It looks like you haven’t activated your account…”** on some pages.

If you see this message, and you have already activated your account, just click the **refresh** button in your browser window. Your account will be activated in the _original_ tab, and the overlay will be removed.

Otherwise, make sure to activate your account using the [Sumo Logic activation email](https://help.sumologic.com/01Start-Here/04Getting-Started/01-How-to-Sign-Up-for-Sumo-Logic).


### "We are unable to ingest the data from the source you specified."

When using the **Upload Files** option from the Setup Wizard it creates a Hosted Collector with the name "File Uploads". If a Hosted Collector with the same name already exists the Setup Wizard will use the existing Collector.

**Upload Files** only works if no other Sources are running on the "File Uploads" Collector. The "File Uploads" Collector can only process one Source at a time.

Do not add Sources to the "File Uploads" Collector, reserve it for the Setup Wizard.
