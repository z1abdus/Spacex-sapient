<h2 align="center">SpaceX Sapient Project</h2>

// Abdus Samad //

![React](https://img.shields.io/badge/react.js-16.3.2-brightgreen.svg)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Overview
Find and explore all of the SpaceX launches to date, including mission details, mission patch, and rocket types.

<p align="center"><img width=95% src="https://lh6.googleusercontent.com/V89XOZPCr1ltFinowOo_dg4SPxHBOVbTeFmlqvCtELbziviR7-ucSDSvz2IlaeqH278N48jrNUAW1tu8LMrP=w2880-h1370-rw"></p>

## Fetch request
This app populates state with data from the SpaceX API through this fetch request in App.js

```javascript
componentDidMount() {
  fetch('https://api.spacexdata.com/v3/launches?limit=100')
  .then(x => x.json())
  .then((launchData) => {
    this.setState({
          launches: launchData,
          filteredCustomers: launchData,
          filteredRockets: launchData
      });
  })
}
```
<br>

## Install
This app requires React and NPM Pacakegs React.  

<br>

https://www.npmjs.com/package/react  

https://www.npmjs.com/package/react-dom  

<br>

After installing dependencies, run a SpaceX-sapient local server. From the app directory...
```javascript
npm start
```

<br>

## Search
Using the 'Search Missions' bar, type a name to search by mission name.
<p align="center"><img width=95% src="https://drive.google.com/uc?id=1M2n8N8uxu58JvCoso3pKxfg4-rr87XD9"></p>

<br>

## Mission Details
Click on the mission patch to display launch details.
<p align="center"><img width=95% src="https://drive.google.com/uc?id=1RSgLJRbI6IRsOiaf_wrE4tNMzG7h13B4"></p>

<br>

## Sort Launch and Land successful missions
Filter out unsuccessful missions with the switch under the search bar.
<p align="center"><img width=95% src="https://lh3.google.com/u/0/d/1wPAz3RP32cKPfoy4bCRiYQFfQE_XkoQw=w2880-h862-iv1"></p>

The below function handles this filter.
```javascript
  handleCheckForLandings = () => {
    fetch('https://api.spacexdata.com/v3/launches?limit=100&land_success=true&launch_success=true')
    .then(x => x.json())
    .then((landData) => {
      this.setState({
        launches : landData,
        filteredCustomers: landData,
        filteredRockets: landData,
        successfulAndLand: !this.state.successfulAndLand,
        });
    });
}
```

<br>

## Filter Land successful missions
Filter out Land successful missions.
<p align="center"><img width=95% src="https://lh3.google.com/u/0/d/1L-FPdBCcLj8zPRVY0vM0gG6IYY8q_6qj=w2880-h1370-iv1"></p>

The below function handles this filter.
```javascript
  handleCheck = () => {
    fetch('https://api.spacexdata.com/v3/launches?limit=100&land_success=true')
    .then(x => x.json())
    .then((landData) => {
      this.setState({
        launches : landData,
        filteredCustomers: landData,
        filteredRockets: landData,
        successfulOnly: !this.state.successfulOnly
      });
    });
  }
```

<br>

## Acknowledgements
SpaceX open and free API  

https://api.spacexdata.com/v3/launches?limit=100

<br>

## License
MIT

<br>
