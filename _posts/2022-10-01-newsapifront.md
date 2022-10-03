---
toc: true
layout: post
description: nba api frontend
categories: [markdown]
title: Rohan G nba api 

<html>
<!-- HTML table fragment for page -->
<table>
  <thead>
  <tr>
    <th>First Name</th>
    <th>Last Name</th>
    <th>Team</th>
    <th>Position</th>
  </tr>
  </thead>
  <tbody>
    <td id="firstname"></td>
    <td id="lastname"></td>
    <td id="team"></td>
    <td id="position"></td>
  </tbody>
</table>

<table>
  <thead>
  <tr>
    <th>Country</th>
    <th>All-time Cases</th>
    <th>Recorded Deaths</th>
    <th>Active Cases</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- generated rows -->
  </tbody>
</table>

<!-- Script is layed out in a sequence (no function) and will execute when page is loaded -->

</html>
<script>
  // prepare HTML result container for new output
  const resultContainer = document.getElementById("result");

  // prepare fetch options
  const url = "http://localhost:8085/api/nba/daily";

  const options = {
    method: 'GET', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, *cors, same-origin
    cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'omit', // include, *same-origin, omit
    headers: {
      'Content-Type': 'application/json'
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
  };

  // fetch the API
  fetch(url, options)
    // response is a RESTful "promise" on any successful fetch
    .then(response => {
      // check for response errors
      if (response.status !== 200) {
          const errorMsg = 'Database response error: ' + response.status;
          console.log(errorMsg);
          const tr = document.createElement("tr");
          const td = document.createElement("td");
          td.innerHTML = errorMsg;
          tr.appendChild(td);
          resultContainer.appendChild(tr);
          return;
      }
      // valid response will have json data
      response.json().then(data => {
          console.log(data);

          // World Data
          document.getElementById("firstname").innerHTML = data.first_name;
          document.getElementById("lastname").innerHTML = data.last_name;
          document.getElementById("team").innerHTML = data.team.division.full_name;
          document.getElementById("position").innerHTML = data.position;
      })
  })
  // catch fetch errors (ie ACCESS to server blocked)
  .catch(err => {
    console.error(err);
    const tr = document.createElement("tr");
    const td = document.createElement("td");
    td.innerHTML = err;
    tr.appendChild(td);
    resultContainer.appendChild(tr);
  });
</script>
