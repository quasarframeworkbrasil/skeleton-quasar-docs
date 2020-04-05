---
description: >-
  In order to configure the structure, there is a folder that centralizes what
  is configurable within the project
---

# Settings \[project\]

The`src/settings`folder has several configuration files. Through them it is possible to configure a series of resources that we will see below.

## `components.js`

Configures the application components in general. Through it we can apply settings to all text fields in the system, for example.

## `date.js`

Handles the date formats and settings that are supported

## `field.js`

It constitutes a field construction factory with all the properties that a field must have.

## `http.js`

HTTP client instance to make connections to the application's base API. It has interceptors and will be changed to pass`headers`and modify the basic connection settings.

## `local.js`

It is the HTTP client instance to make requests for the project itself. It creates a client that points to the URL where the project is available in the browser.

## `report.js`

Represents the settings that can be made to run the reports.

## `rest.js`

It has resources to adapt the`Rest`class communication with the responses that the APIs return.

## `schema.js`

It groups the main properties that we can change when constructing the`schema`and converting a`field`into a [`Vue`](https://vuejs.org)component.

