# General Assembly Project 2 - Asteroid Catasteroid

[Deployed Project Link](https://j-asteroid-catasteroid.herokuapp.com/)

Asteroid was my second project at General Assembly. The main focus of this project was to help develop and practice React.js and AJAX requests/API consumption. This Project was a pair programming exercise done over 48 hours in a pair.

## Task Brief

* **Consume a public API**
* **Have several components**
* **Have a router**
* **Deployed online**

## Technologies Used

* JavaScript (ES6)
* HTML5
* CSS3
* React.js
* Axios
* Git
* Bulma
* Express
* GitHub
* Insomnia
* Flexbox
* Google Fonts
* Nasa Asteroids - NeoWs - [Link](https://api.nasa.gov/)
* Nasa APOD - NeoWs - [Link](https://api.nasa.gov/)

## Installation

* Clone or download the repo
* In the project root install all of project the dependancies with `npm i` 
* In the project room run the command `npm run start`
* Ensure the terminal respondes with 'app is listening on port 4000'
* Open your chosen browser and navigate to `http://localhost:4000/`

## Overview

This project was my first experience of pair programming, using React.js and consuming an API. After doing research on different APIs as a team we decided that we were most fascinated by the NASA APIs and so ended up focussing on their NeoWs (Near earth object web service) API. The core functionality of the website is to give information about the near earth objects any day.

# Walkthrough

## Landing Page
The Landing page is the first page users see and has inputs for the user to enter a valid date. The background is pulled from the NASA Astronomical picture of the day API and so changes on a daily basis.

![Landing page](src/assets/readme/landing.png)

## Loading
The loading page that displays whilst the data is being retrieved.

![Loading](src/assets/readme/loading.png)

## Index Page
The main index page shows up to six of the closest asteroids to earth on the given chosen day

![Loading](src/assets/readme/index.png)

## Extra Functionality

Users are able to click on any of the asteroids displayed and a popup will show with some randomly generated stats about the distance of that object to earth.