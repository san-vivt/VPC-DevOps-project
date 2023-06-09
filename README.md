<h1 align="center">Lab diagram</h1>

_This repository shows a test infrastructure in the AWS cloud._

---

![Image diagram](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/VPC-Test-project.drawio.png)

# Creating a VPC


We will create VPC, 4 Subnets and place the EC-2 instance inside the subnet.

We will also install a webserver on the EC-2 instance and access it using a web browser.

### Quick Check

1\. Create the VPC with the CIDR Block Range 10.0.0.0/16 (65000 Hosts)

2.Create an Internet Gateway and attach it to the newly created VPC

3.Create Public Subnet-1 in Availability Zone-1 with the CIDR 10.0.0.0/24

4.Create Private Subnet-1 in Availability Zone-1 with CIDR of 10.0.1.0/24

5.Create an Elastic IP.

6.Create a NAT Gateway using the Elastic IP and Public Subnet -1 as base

7.Create Public Subnet-2 in Availability Zone-2 with the CIDR 10.0.2.0/24

8.Create Private Subnet-2 in Availability Zone-2 with the CIDR 10.0.3.0/24

9.Update Route Configurations for present Route Table and name it Private Route Table

10.Create Public Route Table and update Route Configurations

11.Create VPC Security Group to allow inbound HTTP,HTTPS and SSH

12.Create EC-2 Instances using the VPC Created as base and the Public Subnet-1 as EC-2 Location.

13.Enable Public IP for the EC-2 

15.Associate the VPC Security Group for the EC-2

14.Update User Data for the EC-2

15.Launch EC-2

16.Test Webserver running on EC-2 using a browser.

After completing the above steps, you can successfully complete this work using the following guide:


### Step by Step Review

1. Create the VPC with the CIDR Block Range 10.0.0.0/16 (65000 Hosts).

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo1.png)

<!---

**1. In the left navigation menu, choose _Elastic IPs_.**
**2. Choose _Allocate Elastic IP_ address.**
**3. On the Allocate Elastic IP address page, leave the settings as is, and choose _Allocate_.**

### In the left navigation menu, choose _VPC Dashboard_.

**1. Choose _Create VPC_.**
**2. For Step 1: _Select a VPC Configuration_, choose _VPC with Public and Private Subnets_.**
**3. **




<h1 align="center">Vue Baremetrics Calendar</h1>

<p align="center">

<img src="https://img.shields.io/badge/made%20by-silentlad-blue.svg" >

<img src="https://img.shields.io/npm/v/vue2-baremetrics-calendar">

<img src="https://img.shields.io/badge/vue-2.6.10-green.svg">

<img src="https://badges.frapsoft.com/os/v1/open-source.svg?v=103" >

<img src="https://img.shields.io/github/stars/silent-lad/Vue2BaremetricsCalendar.svg?style=flat">

<img src="https://img.shields.io/github/languages/top/silent-lad/Vue2BaremetricsCalendar.svg">

<img src="https://img.shields.io/github/issues/silent-lad/Vue2BaremetricsCalendar.svg">

<img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat">
</p>


_A Vue.js wrapper for the beautiful date-range picker made by the **[Baremetrics](https://baremetrics.com)** team._

---

The Vue-Baremetrics date range picker is a simplified solution for selecting both date ranges and single dates all from a single calender view. With a revamped minimalistic redesign.

Redesigned and Wrapped for Vue.js by [Divyansh Tripathi](https://silentlad.com)

# [View a demo](https://silent-lad.github.io/Vue2BaremetricsCalendar/#/)

## [NPM Package](https://npmjs.com/package/vue2-baremetrics-calendar)

<p align="center">
<img src="https://media.giphy.com/media/VFvkCMvXvlTNAGuaZm/giphy.gif">
</p>

# Installation

`npm i --save vue2-baremetrics-calendar`

## Usage

### Global Usage

Global Registeration via Vue.use() method.

```js
// main.js
import Vue from "vue";
import App from "./App.vue";
import router from "./router";
// import the plugin
import Calendar from "vue2-baremetrics-calendar";

Vue.config.productionTip = false;

// use the plugin
Vue.use(Calendar);

new Vue({
  router,
  render: h => h(App)
}).$mount("#app");
```

Once registered you can use the component in its default settings with as follows:-

```html
<Calendar
  type="double"
  @rangeEdit="processDateRange()"
  elementName="doubleRangePicker"
/>

<Calendar
  type="single"
  @dateEdit="processDate()"
  elementName="singleRangePicker"
/>
```

**REMEMBER _elementName_ is the only required prop and it should be different for each datepicker in your component**

```html
<template>
  <div id="app">
    <Calendar
      @rangeEdit="processOutput"
      type="double"
      elementName="otherRangePicker"
    />

    <Calendar
      @dateEdit="processOutput"
      type="single"
      elementName="primaryRangePicker"
    />
  </div>
</template>

<script>
  import Calendar from "./components/Calendar";
  export default {
    components: {
      Calendar
    },
    methods: {
      processOutput(output) {
        console.log(output);
      }
    }
  };
</script>
```

# Events Emitted -

| Name       | Type   | Output                             | Description                      |
| ---------- | ------ | ---------------------------------- | -------------------------------- |
| `dateEdit` | double | [Timestamp(begin), Timestamp(end)] | Array of start date and end date |
| `dateEdit` | single | Timestamp                          | Selected date Timestamp          |

# Base Calendar Props

- **elementName** _\*required_ `[string]`
  - DOM object of the calendar div you're working on
- **earliest_date** `[date YYYY-MM-DD]`
  - The earliest date to show in the calendar
- **latest_date** `[date YYYY-MM-DD]`
  - The latest date to show in the calendar
- **format** `[object]`
  - Object containing formatting strings for.. you guessed it.. formatting your dates
  ```js
    format: {
      input: 'MMMM D, YYYY', // Format for the input fields
      jump_month: 'MMMM', // Format for the month switcher
      jump_year: 'YYYY' // Format for the year switcher
    }
  ```
- **days_array** `[array]`
  - Array of the 7 strings you'd like to represent your days in the calendar
  ```js
  days_array: ["S", "M", "T", "W", "T", "F", "S"];
  ```

### Single Calendar Props

- **current_date** `[date YYYY-MM-DD]`
  - The date to start the calendar on
- **required** `[boolean]`
  - Toggle if this field must have always have a valid selected date
- **placeholder** `[string]`
  - Set placeholder text (note this will only apply if the required key is set to `false`). The default will be whatever moment date format you're using. (i.e. 'M/D/YYYY')

### Double Calendar Props

- **start_date** `[date YYYY-MM-DD]`
  - The date to start the selection on for the calendar
- **end_date** `[date YYYY-MM-DD]`
  - The date to end the selection on for the calendar
- **same_day_range** `[boolean]`
  - Allow a range selection of a single day
- **format** `[preset key in format object] // see above`
  - The double calendar adds the `preset` key to the format object for formatting the preset dates in the preset dropdown
- **presets** `[boolean] or [object]`
  - If you don't want to show the preset link just set this to `false` otherwise the default is true which will just give you a basic preset of.. yep.. presets. BOOM!
  - Otherwise, if you want to customize it up you can include an array of preset objects. Something like:
  ```js
  presets: [
    {
      label: "Last month",
      start: moment()
        .subtract(1, "month")
        .startOf("month"),
      end: moment()
        .subtract(1, "month")
        .endOf("month")
    },
    {
      label: "Last year",
      start: moment()
        .subtract(1, "year")
        .startOf("year"),
      end: moment()
        .subtract(1, "year")
        .endOf("year")
    }
  ];
  ```
-->
