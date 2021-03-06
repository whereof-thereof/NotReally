---
layout: post
title: "The quantifiedSelf (1)"
author: Rob Safar
subtitle: "Measuring and analysing personal consumption"
tags: reports
---

- [iOS Workflow template](https://workflow.is/workflows/3f6cb0a1052d4bdd88e9bb151f82f4c4) (data capture)
- [R scripts](https://github.com/robSafar/quantifiedSelf) (data analysis)

While my iPhone and Apple Watch automatically keep records of certain aspects of my activity, there are other aspects of my life about which I'm curious to learn more than I could otherwise simply intuit. So, I have begun somewhat earnestly to record those other activities and analyse them as data.

In sharing my approach, I have tried to omit all of the details, data and reports of the consumption that I am monitoring. That doesn't preclude ever sharing any such details, and on request I'm happy to provide some dummy data if it helps to illustrate the process better.

The aim of sharing this publicly is two-fold: in order to be open about the *process* of this 'quantified self' data analysis, but also to maintain certain backups that can be easily copied across workstations and devices.

## Data capture

The system relies on human (self-)observation and recording. The [Workflow app](https://itunes.apple.com/us/app/workflow-powerful-automation-made-simple/id915249334) is used to provide an easily-selectable list of common consumption activities (with free-type options) along with automated date/time and postcode location variables. I've made a [duplicate Workflow script](https://workflow.is/workflows/3f6cb0a1052d4bdd88e9bb151f82f4c4) with the list details redacted to show the process involved.

New records are appended to a CSV file stored in iCloud Drive. This platform was selected due to the iPhone's ability to store the file locally, modify it offline and upload to the iCloud later on. This ensures that data can still be captured in the absence of an active internet connection.

## Analysis

The analysis uses the statistical computing and graphics environment [R](https://cran.r-project.org). The [knitr](https://cran.r-project.org/web/packages/knitr/index.html) package is required to use the R Markdown reporting script, and [ggplot2](https://cran.r-project.org/web/packages/ggplot2/index.html) is used as a quick and flexible plotting system.

All of the processing and analysis code can be found in my [quantifiedSelf GitHub repository](https://github.com/robSafar/quantifiedSelf). Knitting the `report.Rmd` file produces an HTML report: pulling the data directly from my local iCloud Drive Workflow folder, cleaning it, backing it up in the repository folder and then generating the report. A separate `script.R` script is used for the basic pre-plotting processing, which is strictly for ease of development - before exploring the data I can simply source that script rather than repeat some of the basic steps it executes.

At some point other datasets may be merged and analysed with this, such as sleep and activity tracking (via [Sleep Cycle](https://itunes.apple.com/gb/app/sleep-cycle-alarm-clock/id320606217) and Apple's Activity apps respectively), for a larger, multi-dimensional analysis.

In the meantime, I'll keep the [GitHub repo](https://github.com/robSafar/quantifiedSelf) updated and write up any significant developments.

* * *

***Update:** I've combined this dataset with health/activity information, providing a very quick chart showing the relationship between active calorie burning and the various consumption activities. Grabbing the data from Apple's system involves going via an XML file, which makes processing significantly longer. It seems worth it though, adding a whole new dimension to the report.*
