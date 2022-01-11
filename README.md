<h1 align="center">Tastebook - Project 3</h1>

<p align="center">
<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641837266/tastebook_1_sozy68.png" height="500">
<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641837266/tastebook_2_q2kqe7.png" height="500">
</p>

## Table of Contents:

1. [Project Overview](#project-overview)
2. [Deployment](#deployment)
3. [Getting Started](#getting-started)
4. [Project Brief](#project-brief)
5. [Technologies used](#technologies-used)
6. [Development Process and Timeline](#development-process-and-timeline)
7. [Bugs](#bugs)
8. [Challenges](#challenges)
9. [Wins](#wins)
10. [Key Learnings](#key-learnings)
11. [Future Improvements](#future-improvements)

## Project Overview

Tastebook is a full stack application, built in 8 days as part of a group project during Software Engineering Immersive course. It is a complex MERN stack recipe app, allowing registered users to share, edit, review, like, comment and rate recipes.

## Deployment

The application was deployed through Heroku, using MongoDB Atlas to host data in the cloud.

You will find the deployed app here: [Tastebook](https://tastebook-yem.herokuapp.com/)

Register and login to explore the app.

## Getting Started

1. Clone or download the repo
2. Install the project's dependencies:

```
yarn install
```

3. Start the database by running:

```
mongod --dbpath ~/data/db
```

4. Seed the back-end server:

```
yarn seed
```

5. Initialise the back-end server:

```
yarn serve
```

6. Start the server by running:

```
nodemon
```

7. Go to frontend folder:

```
cd frontend
```

8. Run the frontend using:

```
yarn start
```

## Project Brief

- Build a full stack MERN based application in a group of 3 in 8 days
- Use an Express API to serve data from MongoDB
- Build a front-end with React to consume our own built API
- Create multiple relationships and CRUD functionality
- Create wireframes to help with project design and features
- Deploy the project so it's publicly accessible.

## Technologies used

- Back-end:
  - Node.js
  - Mongodb
  - Mongoose
  - Express
  - Bcrypt
  - JWT
- Frontend:
  - React.js
  - Axios
  - SCSS
- Development tools:
  - VS code
  - Yarn
  - Insomnia
  - Git + Github
  - Heroku (deployment)
  - Asana (planning and timeline)

## Development Process and Timeline

### Timeline:

- Day 1 - Project planning
- Day 2-3 - Back-end
- Day 3-7 - Front-end
- Day 8 - Styling

### Day 1 - Project Planning:

Once we agreed on the initial idea of the app, we wrote down the features we wanted to implement, planned the back-end and the front-end accordingly and looked for design inspiration by visiting the most popular recipe apps.
We have decided to implement three models - recipe, user and comments, and embedded relationships for recipe likes and average rating,and user liked and created recipes. As soon as we had a clear plan for the back-end we agreed on the front-end features and layout, we created wireframes and worked on task division using Asana to help reach our goals in time.

Wireframe:

<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641903118/github/Blank_diagram_uzsif0.png" width="=800">

We have agreed to do group coding taking turns for back-end implementation and split front-end implementation into tasks assigned in advance. As a group we set out our working hours and scheduled daily stand ups to review the progress, wins and any potential blockers through Zoom and Slack. Stand up time was also used to merge work onto GitHub and resolve any conflicts arising.

<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641837266/tastebook_4_ol7ain.png" width="700">

### Day 2-3 - Back-end

First of all we have created a recipe model to include desired fields and defined the type of input for each field. Same approach was taken to define comments and user models. Knowing the features we were looking to implement, we have established embedded and virtual relationships under recipe schema to display comments, number of likes and average rating, while virtual relationships under user model were created to display user created, liked and rated recipes.

<p><img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641898132/github/tastebook_6_v3vmpo.png" height="500">
<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641898137/github/tastebook_5_bk6xpx.png" height="250"></p>

Once models and relationships were defined, we have moved onto CRUD functionality, authorisation and router implementation with secure routes for editing, creating, liking, deleting and rating of recipes. We used Insomnia to test back-end and see if embedded and virtual schema's were populated with the correct information.

### Day 3-7 - Front-end

On day 3 we worked together to set up the front end by installing React with the dependencies we would all initially require to get going on our own sections and linked the front-end and the back-end using HTTP-proxy-middleware. From there on, each of us focused on the tasks assigned during the planning stage. I have contributed to the project by creating individual recipe cards, recipe list in the browsing section, individual recipe page, implementation of comments and ratings and extraction of recipes from publicly accessible database in order to seed ours and save time not having to do it manually. We have agreed to have all the functionality implemented by the end of day 7 and leave additional features if there is time remaining. Although the final day was dedicated for styling, some of it had to be completed as we went along to help visualise the progress.

### Recipe Card and List

When creating a recipe card, I wanted to display recipe title, image, number of likes, average rating, cooking time and difficulty level. React icons were used to replace some of the text and give cards a simplistic look.
Axios was used for API requests to fetch recipes and generate a list by mapping through all the recipes in the database and displaying them as cards.

### Individual Recipe Page

React useEffect and useState hooks were used to fetch, set and display recipe information such as ingredients, method, reviews, number of likes, average rating etc. Since each step of the recipe method as well as each ingredient is added as a list item in the array, I have displayed it using map operator.
Certain features such as recipe editing and an option to delete a recipe were set up to only be displayed if the user is logged in and is the owner of the recipe in order to protect recipe owner posts and the app content as a whole.

<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641898132/github/tastebook_7_h6eq0l.png" height="350">

### Comments and rating

I used React rating stars component to allow users rate recipes in the scale from 1 to 5, when logged in. Stars highlight in yellow when hovered over to display the rating given. Feature was set up to request users to submit a comment in order to rate recipes and vice versa. Code included error handling.

<p><img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641898131/github/tastebook_8_crbksl.png" height="250">
<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641898131/github/tastebook_9_pcmlbo.png" height="250"></p>

### Database seeding

In order to save time when seeding the app database and avoid the option of adding recipes one by one, I have used a publicly accessible database to extract recipes in the format set out under recipe schema. To do so, I have written a python script that takes in the data from downloaded dataSet.csv file and dumps the information in recipes.json file in the defined format. Since some fields such as cookTime, prepTime, difficulty and others were not defined in the public database but were set as mandatory in our recipe schema, I have used a random selection of options provided to generate the information. Once recipes were extracted, information dumped in recipes.json file was copied over to the seeds file to seed our database, giving the app a complete look.

<img src="https://res.cloudinary.com/eevelynaa1/image/upload/v1641899401/github/Screenshot_2022-01-11_at_11.09.16_u4jumm.png" height="500">

### Day 8 - Styling

Although we initially planned to use SASS and ReactBootstrap to style our project, having the basic styling in place applied using CSS and due to time constraints we have decided to avoid the risk of having to redo most of it and decided to finish it off using CSS. Since we were already working on separate pages, we have split styling according to the pages and components we were implementing. Our app logo was designed to reflect the simplicity of the overall app look, adding a nice touch for the branding.

## Bugs

Nav bar requires some formatting as it is currently shifting all the content to the right hand side when displayed on a mobile view. It has also been noted that the updated recipe page does not always re-render after an update and still displays old information.

## Challenges

Since it was our first time building a full stack project as a group, it took time to get comfortable with merging work on GitHub and resolving conflicts, which by the end of the week has become our daily routine.
At the start I found it quite challenging to visualise and understand on how to implement commenting and rating features and display average rating as part of a virtual relationship created in the back-end. However, this project was a perfect opportunity to solidify the knowledge gained in class.

## Wins

- Planning has helped us to focus on the prioritised tasks and implement features required to present a functional app.

- We were very happy with the features we have implemented and having had time for some that were not initially present on the priority list.

- The overall look was another win. We seeked inspiration and displayed the content in user friendly, simplistic and clean format.

## Key Learnings

This project was the most complex project I have ever had a chance to build, bringing together everything we'd learnt on the course so far. It was also a great opportunity to learn working as a team, which allowed us to discuss issues, seek advice and troubleshoot together instead of doing it on our own, which sometimes could take up a lot of time and feel quite isolating. I believe that careful planning, ownership of responsibilities and communication throughout the project has helped us to meet our goal in the set timeframe.

## Future Improvements

- Search/filter feature to help users find what they are looking for quickly.
- Some of the code could be refractured to make it easier to read.
- Add an option for the user to upload a picture which could be displayed on the profile page and users comments.
- Fix navigation bar styling to avoid it from shifting the content underneath and finish off homepage styling to give it more of a defined look.
