<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://bp-gc.in/kotak-refs">
    <img src="https://user-images.githubusercontent.com/39854726/132136134-db22d5da-cfa6-4791-96da-094214a98dde.png" alt="Logo" width="80" height="80">
  </a>

  <h1 align="center">KEF Volunteering App</h1>

  <p align="center">
    A full-stack mobile application made for the Kotak Education Foundation as part of my virtual internship in the Summer of 2021. 
    <br />
    <a href="https://drive.google.com/file/d/1R_HgGJGehIbOtvHcfdgtbMYTitb6dw11/view?usp=sharing"><strong>View the Project Report »</strong></a>
    <br />
    <br />
    <a href="https://drive.google.com/file/d/1fhqfnFTph3maDRnhcM7YmYoQp1nGF_UG/view?usp=sharing">Download Demo APK</a>
    <br />
	This repository contains the server-side code of the application, written in Node. The code for the front-end is available <a href="https://github.com/shameekbaranwal/KEF-Volunteering">here</a>.
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#about-the-api">About the API</a>
      <ul>
        <li><a href="#interaction-with-sheets">Interaction with Sheets</a></li>
        <li><a href="#authentication">Authentication</a></li>
        <li><a href="#endpoints">Endpoints</a></li>
      </ul>
    </li>
    <li><a href="#project-report">Project Report</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Kotak Education Foundation (KEF) is an NGO operating in the space of education and livelihood since 2007. Its primary focus is to help poor children and youth to be empowered through education and livelihood respectively. <br/> <br/>
A major hurdle with the management of such a vast range of activities and people from different backgrounds, especially remotely, was that there was no efficient way set up to communicate details about various activities from Volunteers to Beneficiaries and vice-versa. Being that both Volunteers and Beneficiaries generally come from non-technical backgrounds, several tasks, like filling important forms regularly, became quite inconvenient and unnecessarily complicated, which hindered the efficiency of the programmes. The KEF Members had to manually call each volunteer and beneficiary to inform them of the upcoming scheduled activities and sessions, and then call them again for their feedback on whatever activity they conducted or attended.
<br/> <br/>
As interns, our methodology for solving this critical problem was simple - we created a mobile application that serves as a one-stop for both Volunteers and Beneficiaries, as well as any third party Intervention managers. This application consists of the several forms that were previously spread out across various links, and allows a user to find what they want easily. The app also allows new members to Sign Up and Join the KEF as either a Volunteer or a Beneficiary.
<br/><br>
<strong>This repository contains the server-side code of the application, written in Node. The code for the front-end is available [here](https://github.com/shameekbaranwal/KEF-Volunteering).</strong>

### Built With

* [Node](https://nodejs.org/)
* [Express](https://expressjs.com/)
* [Sheets API](https://developers.google.com/sheets/api)


<!-- GETTING STARTED -->
## About the API

This API was created to serve as a middleman for the app's front-end (code available [here](https://github.com/shameekbaranwal/KEF-Volunteering)) and the Google Sheets database. More information about its features are discussed below.

### Interaction with Sheets

In order to authorize the server to access the Google Sheet, we made use of OAuth2 with Sheets API v4. This was done using a custom configured service account created using the Google Developers Console. This allowed us to maintain a primary Google Sheet as the live database for this application. 

### Authentication

6 / 9 endpoints in this API are protected, as they allow a user to directly access the database. For protecting the mentioned endpoints, we used JSON Web Tokens. The server will handle these protected endpoint requests using an authentication middleware, which will verify the received tokens against the key that it used to generate and sign tokens. Only if the token is found to be valid and un-expired, the server forwards the request ahead to the next function in the request handling pipeline. In this manner, an unauthorized client cannot just make requests to the server to extract or manipulate the data in the official Google Sheets database. Only a user with a valid JSON Web Token obtained after submitting a valid email and phone can make readable requests to the
server. Otherwise the server will respond with a <strong>401 Unauthorized</strong> status to the client.


### Endpoints

The API has nine available endpoints:  
	<ul>
		<li>POST <strong>/api/login</strong></li>
		<li>POST <strong>/api/register/volunteer</strong></li>
		<li>POST <strong>/api/register/beneficiary</strong></li>
		<li>POST <strong>/api/logsheet</strong></li>
		<li>POST <strong>/api/feedback/volunteer</strong></li>
		<li>POST <strong>/api/feedback/beneficiary</strong></li>
		<li>POST <strong>/api/feedback/intervention</strong></li>
		<li>POST <strong>/api/events</strong></li>
		<li>GET <strong>/api/events</strong></li>
	</ul>

## Project Report

Further details regarding the functionality and codebase of the application project is available in the project report available [here](https://bp-gc.in/kotak-refs).