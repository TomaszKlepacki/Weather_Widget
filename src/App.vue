
<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;900&family=Oswald:wght@300;400;500;700&family=Red+Hat+Display:wght@300;400;500;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: 0;
}

body {
  font-family: 'Red Hat Display';
}

#app {
  background-image: url('./assets/cold-bg.jpg');
  background-size: cover;
  background-position: bottom;
  transition: 0.5;
}

main {
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 1, 0.9));
}

.heading {
  text-align: center;
  margin: 75px auto 30px;
  text-transform: uppercase;
  color: white;
}

.search {
  align-content: center;
  max-width: 30vw;
  margin-bottom: 30px;
  margin: auto;
}

.search .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;
  font-weight: 500;
  border: none;
  outline: none;
  background: none;
  border: white 2px solid;
  text-transform: capitalize;
  box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 25px;
  transition: 0.4s;
  font-weight: 600;
}

.search .search-bar:focus {
  box-shadow: 0px 0px 16px;
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 0px 25px 0px 25px;
}

.button {
  margin: 25px auto;
  align-content: center;
  background-color: #0169BB;
  border: white 2px solid;
  border-radius: 25px;
  box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.25);
  color: white;
  padding: 10px 32px;
  text-align: center;
  text-decoration: none;
  display: block;
  font-size: 20px;
  font-weight: 600;
  cursor: pointer;
  transition: 0.3s;
}

.button:hover {
  background-color: white;
  border: #0169BB 2px solid;
  color: #0169BB;
}

.location-box .location {
  margin-top: 30px;
  color: white;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: white;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
}

.content-table {
  align-items: center;
  border-collapse: collapse;
  margin: 25px auto;
  font-size: 0.9em;
  min-width: 400px;
  border-radius: 20px 20px 0 0;
  overflow: hidden;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.6);
}

.content-table thead tr {
  background-color: #0169BB;
  color: white;
  text-align: left;
  font-weight: bold;
}

.content-table th, .content-table td {
  padding: 12px 15px;
}

.content-table tbody tr {
  border-bottom: 2px solid #dddddd;
  background-color: #f3f3f3;
}

.content-table tbody tr.active-row {
  font-weight: bold;
  color: #0169BB;
}
</style>
