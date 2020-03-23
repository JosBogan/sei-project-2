# General Assembly Project 2 - Asteroid Catasteroid

[Deployed Project Link](https://j-asteroid-catasteroid.herokuapp.com/)

Asteroid Catasteroid was my second project at General Assembly. The main focus of this project was to help develop and practice React.js and AJAX requests/API consumption. This Project was a pair programming exercise done over 48 hours in a pair.

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
* In the project root install all of project the dependencies with `npm i` 
* In the project room run the command `npm run start`
* Ensure the terminal responds with 'app is listening on port 4000'
* Open your chosen browser and navigate to `http://localhost:4000/`

## Overview

This project was my first experience of pair programming, using React.js and consuming an API. After doing research on different APIs as a team we decided that we were most fascinated by the NASA APIs and so ended up focussing on their NeoWs (Near earth object web service) API. The core functionality of the website is to give information about the near earth objects any day.

# Walkthrough

## Landing Page
The Landing page is the first page users see and has inputs for the user to enter a valid date. The background is pulled from the NASA Astronomy picture of the day API and so changes on a daily basis.

![Landing page](src/assets/readme/landing.png)

## Loading
The loading page that displays whilst the data is being retrieved.

![Loading](src/assets/readme/loading.png)

## Index Page
The main index page shows up to six of the closest asteroids to earth on the given chosen day.

![Loading](src/assets/readme/index.png)

## Extra Functionality

Users are able to click on any of the asteroids displayed and a popup will show with some randomly generated stats about the distance of that object to earth.

## Process
1. We spent the first couple of hours looking through the public API's and deciding on one to use
2. Tested the API endpoints in Insomnia and made sure that we could obtain and understood the data being pulled through
3. We then started wireframing the design and functionality of the website.
4. Started planning the code for each page and some high level pseudocoding.
5. Built out the landing page and request functionality
6. Developed the main index page of the application.

# Reflections

## Featured Code

The following code is part of the AsteroidCard component that renders an individual asteroid on the index page. As it was my first project utilizing React.js and JSX I was happy with how all of the conditional rendering came through. The array of asteroids is being mapped over and then for each one, this component is being rendered, with the asteroid data being passed down as props. There are also a couple of conditions to check if the asteroid passed down is the asteroid closest to earth on that day, which was passed down through the `large` prop.

```JSX
render() {
  const data = this.props.close_approach_data[0]
  return (
    <div onClick={this.calcDist} className="innerCardContainer dist_head">
      <div className="Header">
        <h2 className="is-size-4 has-text-weight-semibold">{this.props.large ? 'Danger' : 'Safe'}</h2>
        {this.props.large && <p className="is-size-7">- Distance from you -</p>}
        <h4 className="is-size-6 ">{parseInt(data.miss_distance.kilometers).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')} km</h4>
      </div>
      <div className="rule"></div>
      <div className="contentBox">
        <h3><span className="has-text-weight-semibold">Name:</span> {this.props.name.replace(/[()]/gi, '')}</h3>
        <h4><span className="has-text-weight-semibold">Size:</span> {(this.averageSize())} meters</h4>
        <h4><span className="has-text-weight-semibold">Speed:</span> {parseInt(data.relative_velocity.kilometers_per_second)} km/s</h4>
        <h4><span className="has-text-weight-semibold">Time:</span>  {
          data.close_approach_date_full ? 
            data.close_approach_date_full.split(' ')[1] :
            'NA 😞'}</h4>
      </div>
    </div>
  )
}
```

Due to the heavily nested nature of the API we chose to use, trying to sort the asteroids by distance ended up being quite laborious. I am happy with how it turned out in the end however.

```javascript
sortData = (data) => {
  const selectedDate = `${this.state.url}`
  const newData = data[selectedDate].sort((a,b) => {
    return (
      parseInt(a.close_approach_data[0].miss_distance.kilometers) - parseInt(b.close_approach_data[0].miss_distance.kilometers)
    )
  })
  newData.length = 6
  return newData
}
```

## Wins

I am very happy with how the project all came together. There were a couple of different ways that we could have routed the user from the landing page to the index page and sent a request to the API but the current set up allows users to not only enter the date in the inputs given but also works if the date is entered directly into the URL bar.

## Challenges

I think that the biggest challenge for us in this Project was getting to grips with the NASA NeoWs API. We got caught out on numerous occasions by the structure of the data sent and what the data actually represented. We also came across a couple of unexpected issues, one being that occasionally NASA's Astronomy picture of the day API sends a video instead of a picture, which would break our background. We managed to fix this with a simple check to see if the url of the link received through the data was to a video and setting a default image if the link if so.
```javascript
this.setState({ background: !res.data.hdurl ? 'https://apod.nasa.gov/apod/image/2001/IntoTheShadow_apod.jpg' : res.data.hdurl })
```

Another problem that we came across was that for design purposes we chose not to use the date input picker but this means that we had to account for the format people would enter their dates. The NeoWs API requires a format of `2004-07-02` whilst the number input would allow for `2004-7-2`, which would get no data back from the API.

## What Next

If I were to take this project further I would probably attempt to add more functionality to create a more robust application such as:

* Allow for date ranges.
* Add more calculations to allow for better calculations of the most dangerous asteroid in the list (currently it is just based on distance).
* Add the ability to skip back or forwards one day easily

## Key Learnings

My main take away from this project was one about pair programming. Having never had to really explain my reasoning or code to anyone else before, at the start I found it very difficult to vocalise what the logic I was thinking of. This project really opened my eyes to this and also how much it can help to have another person to bounce ideas off. 

