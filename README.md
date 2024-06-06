# Calculator for Acute Rheumatic Fever

**NOTE: This is experimental software and is not approved for diagnostic purposes.**

This is a browser-based (html and javascript) application providing a user friendly implementation of the 2020 Australian criteria for Acute Rheumatic Fever diagnosis.  

Acute Rheumatic Fever (ARF) develops as the result of an autoimmune response following a Group A Streptococcal bacterial infection. Severe or repeated occurrences of ARF can result in long term cumulative heart valve damage referred to as Rheumatic Heart Disease.  Correct diagnosis of ARF is essential to mitigate the risk of such occuring.

This single page application can be built using NodeJS, the Vue 3 framework, and Vuetify UI Library to create the necessary HTML and Javascript that may then be deployed directly on a web server.

## Important Links

- [2020 Updated Australian criteria for ARF diagnosis](https://www.rhdaustralia.org.au/system/files/fileuploads/a3_2020_updated_criteria_for_arf_diagnosis.pdf)
- [Vuetify Component Framework](https://vuetifyjs.com/en/)
- [The Progressive Javascript Framework](https://vuejs.org/)

## Deployment

### Install NodeJS

If you do not already have NodeJS installed, you will need to download and install this as a pre-requisite for further steps.   You can get an installer [here](https://nodejs.org/en/download/prebuilt-installer).

### Install Vue

To install Vue3, open a command line window, and run the following command:

```npm install vue@next
```

### Clone the Application Repository

To clone the repository and change into the new application folder, open a command line window, and run the following commands:

```git clone https://github.com/dfoulkesjcu/arf-rhd-calculator.git
cd arf-rhd-calculator
```

### Install Vuetify plugin

To install the Vuetify plugin, open a command line window, change to the application folder, and run the following command:

```npm install vuetify@latest
```

### Starting the Development Server

To start the development server, open a command line window, change to the application folder, and run the following command:

```npm run dev
```

The server will be accessible at [http://localhost:3000](http://localhost:3000):

### Building for Depoloyment

To ready the application for deployment on a production server, open a command line window, change to the application folder, and run the following command:

```npm run build
```

Once the process is completed, build content can be found in the **dist** folder.    

The application may now be deployed to a production environment by means of copying all files and folders from the dist folder to the production web server.

## Support Ongoing Development

This software has been developed by Northern Australian Regional Digital Health Collaborative (NARDHC).  Any feedback or support to enhance this will be appreciated.

## 📑 License
[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2024-present Daniel Foulkes, Northern Australian Regional Digital Health Collaborative
