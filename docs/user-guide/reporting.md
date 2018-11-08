---
layout: docwithnav
title: Reporting
description: Reporting Guide
---

# reporting

* TOC

  {:toc}

### Overview

ThingsBoard allows you to generate reports using existing dashboards.

Reports can be generated either from the currently opened dashboard or scheduled using the [Scheduler](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/scheduler/README.md#generate-report) capabilities.

![image](../../.gitbook/assets/reporting.svg)

### Reports Server

The Reports Server is a standalone service used to generate reports by rendering dashboards in a headless browser.

On each generate report request, ThingsBoard node sends a request to the Reports Server using the configured endpoint URL.

The Reports Server opens a web page with the target dashboard URL in the headless browser and waits until the page renders, then it captures the dashboard web page into the specified format \(_PDF \| PNG \| JPEG_\) and sends the captured data as a response to ThingsBoard.

The system administrator can configure the Reports Server endpoint URL using [thingsboard.yml](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/config/README.md).

The following is a sample configuration:

```yaml
# Reports parameters
reports:
  server:
    endpointUrl: "${REPORTS_SERVER_ENDPOINT_URL:http://localhost:8383}"
```

### Generate Report from Dashboard

The Tenant Administrator or Customer User can generate a report from the currently opened dashboard.

* Click the **Export Dashboard** button located at the right side of the dashboard toolbar

![image](../../.gitbook/assets/reporting-export-dashboard-button.png)

* In the expanded drop-down menu, select the desired dashboard export option

![image](../../.gitbook/assets/reporting-export-dashboard-options.png)

* The report generation will start.

![image](../../.gitbook/assets/reporting-export-dashboard-progress.png)

* And finally, the report file will be automatically downloaded in the format selected.

### Generate Report by schedule

Report generation can be invoked by a schedule using the [**Generate Report** Scheduler Event](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/scheduler/README.md#generate-report).

### Generate Report Rule Chain

Scheduled reports generation is supported by the default **Root Rule Chain** of ThingsBoard PE. By default, a message of type **Generate Report** is routed to the **Generate Report Rule Chain**.

![image](../../.gitbook/assets/reporting-pe-root-rule-chain-switch.png)

The **Generate Report Rule Chain** has a [**Generate Report** Rule Node](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/pe/action-nodes/README.md#generate-report-node) that performs the report generation according to the report configuration retrieved from the message body.

If the message body has a field `sendEmail` and its value is set to `true`, the message with a report file reference in the `attachments` field of the metadata will be routed to the email related Rule Nodes. The Email Rule Nodes will prepare the email message with a report file in the attachments and send it to the configured recipients.

![image](../../.gitbook/assets/reporting-generate-report-rule-chain.png)

### Reports Widget

ThingsBoard provides access to the generated report files via the **Reports** Widget that is a part of the **Files** Widgets Bundle.

![image](../../.gitbook/assets/reporting-reports-widget.png)

The widget has the ability to filter the reports using the time range component.

Also, the widget has the ability to search the reports by name.

Each report can be downloaded by clicking on the **Download file** button.

## Next steps

