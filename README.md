<a id="readme-top"></a>
<div align="center">
  <a href="https://github.com/dfoulkes-au/arf-rhd-calculator"><img src="public/favicon.ico" alt="ARF Logo" width="80" height="80"></a>
  <h2>Calculator for Acute Rheumatic Fever (Experimental) - Code Package</h2>
</div>


## Overview

This project includes the code for a browser-based application providing a user friendly implementation of the 2020 Australian criteria for Acute Rheumatic Fever diagnosis - based on Revised Jones Criteria for the Australian context.

The code in this project describes a single page application that can be built using NodeJS, the Vue 3 framework, and Vuetify UI Library to create the necessary HTML and Javascript that may then be deployed directly on a web server.  The primary use of this project is for those who wish to integrate this with an existing web application and/or to modify its function or UI.

[Here](https://arf-calculator.nardhc.org/) is a deployed example of the ARF Calculator.

**NOTE: This is experimental software and is not approved for diagnostic purposes.**

If you simply wish to deploy the web application without modification,  go to [Acute Rheumatic Fever Calculator - Deployment Package](https://github.com/dfoulkes-au/arf-rhd-calculator-dist) where you can access the html/js files required.

If you like this, don't forget to give the project a star! Thanks again!

## Background

Acute rheumatic fever (ARF) results from the body’s autoimmune response following an infection with Group A Streptococcus bacterium (Streptococcus pyogenes). Rheumatic heart disease (RHD) refers to the long-term cardiac damage caused by either a single severe episode or multiple recurrent episodes of ARF.  The development of ARF occurs approximately two weeks after S. pyogenes infection . The clinical manifestations and symptoms of ARF can be severe and are described in the Revised Jones Criteria[^1].

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

If you wish to modify the code in this project it is recommended that you are familiar with the Vue Framework, Javascript and HTML.  Some familiarity with Vuetify UI library is also helpful.

You will also need to install and configure the following software (if not already installed).

### Node.js

If you do not already have NodeJS installed, you will need to download and install this as a pre-requisite for further steps.   You can get an installer [here](https://nodejs.org/en/download/prebuilt-installer).

### Vue

To install Vue3, open a command line window, and run the following command:

```sh
npm install vue@next
```

### Clone the Application Repository

To clone the repository and change into the new application folder, open a command line window, and run the following commands:

```sh
git clone https://github.com/dfoulkes-au/arf-rhd-calculator.git
cd arf-rhd-calculator
```

### Install Vuetify plugin

To install the Vuetify plugin, open a command line window, change to the application folder, and run the following command:

```sh
npm install vuetify@latest
```

### Starting the Development Server

To start the development server, open a command line window, change to the application folder, and run the following command:

```sh
npm run dev
```

The server will be accessible at [http://localhost:3000](http://localhost:3000):

### Modifying the code

Using a text editor or IDE,  you can the .vue files in the src/components folder and various other text based files and folders.  

Although the development server may detect and update web pages after you have made changes, it may sometimes be necessary to restart the development server.

### Building for Depoloyment

To ready the application for deployment on a production server, open a command line window, change to the application folder, and run the following command:

```sh
npm run build
```

Once the process is completed, build content can be found in the **dist** folder.

The application may now be deployed to a production environment by means of copying all files and folders from the dist folder to the production web server.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Support Ongoing Development

This software has been developed by Northern Australian Regional Digital Health Collaborative (NARDHC).  Any feedback or support to enhance this will be appreciated.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also open an issue with the tag "enhancement".

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/MyFeature`)
3. Commit your Changes (`git commit -m 'Add to NewFeature'`)
4. Push to the Branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

## About the Project

### License

Distributed under the MIT License. See [LICENSE.md][license-url] for more information.

### Acknowledgments and Links

- [2020 Updated Australian criteria for ARF diagnosis](https://www.rhdaustralia.org.au/system/files/fileuploads/a3_2020_updated_criteria_for_arf_diagnosis.pdf)
- [Vuetify Component Framework](https://vuetifyjs.com/en/)
- [The Progressive Javascript Framework](https://vuejs.org/)

### Contacts

- [Northern Australian Regional Digital Health Collaborative][linkedin-nardhc-url]
- [Daniel Foulkes][linkedin-df-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[linkedin-df-url]: https://www.linkedin.com/in/daniel-foulkes/
[linkedin-nardhc-url]: https://www.linkedin.com/company/101721851
[license-url]: https://github.com/dfoulkes-au/arf-rhd-calculator/blob/main/LICENSE.md
