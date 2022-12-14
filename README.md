# FoundAmoeba
 Challenge-18-NoSQL-Social-Network-API

## Your Task
MongoDB is a popular choice for many social networks due to its speed with large amounts of data and flexibility with unstructured data. Over the last part of this course, you’ll use several of the technologies that social networking platforms use in their full-stack applications. Because the foundation of these applications is data, it’s important that you understand how to build and structure the API first.

Your challenge is to build an API for a social network web application where users can share their thoughts, react to friends’ thoughts, and create a friend list. You’ll use Express.js for routing, a MongoDB database, and the Mongoose ODM. In addition to using the Express.js (https://www.npmjs.com/package/express) and Mongoose (https://www.npmjs.com/package/mongoose) packages, you may also optionally use a JavaScript date library of your choice or the native JavaScript Date object to format timestamps.

Because this application won’t be deployed, you’ll also need to create a walkthrough video that demonstrates its functionality and all of the following acceptance criteria being met. You’ll need to submit a link to the video and add it to the README of your project.

There is no starter code for this project.

## User Story
* AS A social media startup
* I WANT an API for my social network that uses a NoSQL database
* SO THAT my website can handle large amounts of unstructured data

## Acceptance Criteria
* GIVEN a social network API
* WHEN I enter the command to invoke the application
* THEN my server is started and the Mongoose models are synced to the MongoDB database
* WHEN I open API GET routes in Insomnia for users and thoughts
* THEN the data for each of these routes is displayed in a formatted JSON
* WHEN I test API POST, PUT, and DELETE routes in Insomnia
* THEN I am able to successfully create, update, and delete users and thoughts in my database
* WHEN I test API POST and DELETE routes in Insomnia
* THEN I am able to successfully create and delete reactions to thoughts and add and remove friends to a user’s friend list

## Mock-Up
The following animations show examples of the application's API routes being tested in Insomnia.

The following animation shows GET routes to return all users and all thoughts being tested in Insomnia:

![Mock-Up Gif One](./public/images/mock-up-gif-one.gif?raw=true "Mock-Up Gif One")

The following animation shows GET routes to return a single user and a single thought being tested in Insomnia:

![Mock-Up Gif Two](./public/images/mock-up-gif-two.gif?raw=true "Mock-Up Gif Two")

The following animation shows the POST, PUT, and DELETE routes for users being tested in Insomnia:

![Mock-Up Gif Three](./public/images/mock-up-gif-three.gif?raw=true "Mock-Up Gif Three")

In addition to this, your walkthrough video should show the POST, PUT, and DELETE routes for thoughts being tested in Insomnia.

The following animation shows the POST and DELETE routes for a user’s friend list being tested in Insomnia:

![Mock-Up Gif Four](./public/assets/mock-up-gif-four.gif?raw=true "Mock-Up Gif Four")

In addition to this, your walkthrough video should show the POST and DELETE routes for reactions to thoughts being tested in Insomnia.

## Getting Started
Use the following guidelines to set up your models and API routes:

## Models
User
* username
- String
- Unique
- Required
- Trimmed

* email

- String
- Required
- Unique
- Must match a valid email address (look into Mongoose's matching validation)

* thoughts

Array of _id values referencing the Thought model

* friends
- Array of _id values referencing the User model (self-reference)

Schema Settings

Create a virtual called friendCount that retrieves the length of the user's friends array field on query.

___________________________

Thought

* thoughtText

- 
- String
- Required
- Must be between 1 and 280 characters

* createdAt

- Date
- Set default value to the current timestamp
- Use a getter method to format the timestamp on query

* username (The user that created this thought)

- String
- Required

* reactions (These are like replies)

- Array of nested documents created with the reactionSchema

Schema Settings

Create a virtual called reactionCount that retrieves the length of the thought's reactions array field on query.

________________________________

Reaction (SCHEMA ONLY)

* reactionId
- Use Mongoose's ObjectId data type
- Default value is set to a new ObjectId

* reactionBody
- String
- Required
- 280 character maximum

* username
- String
- Required

* createdAt
- Date
- Set default value to the current timestamp
- Use a getter method to format the timestamp on query

Schema Settings

This will not be a model, but rather will be used as the reaction field's subdocument schema in the Thought model.

* API Routes
/api/users
- GET all users
- GET a single user by its _id and populated thought and friend data
- POST a new user:

// example data
{
  "username": "lernantino",
  "email": "lernantino@gmail.com"
}

- PUT to update a user by its _id
- DELETE to remove user by its _id

BONUS: Remove a user's associated thoughts when deleted.

__________________________________________

/api/thoughts

- GET to get all thoughts
- GET to get a single thought by its _id
- POST to create a new thought (don't forget to push the created thought's _id to the associated user's thoughts array field)

// example data
{
  "thoughtText": "Here's a cool thought...",
  "username": "lernantino",
  "userId": "5edff358a0fcb779aa7b118b"
}

- PUT to update a thought by its _id
- DELETE to remove a thought by its _id

__________________________________________

/api/thoughts/:thoughtId/reactions

- POST to create a reaction stored in a single thought's reactions array field
- DELETE to pull and remove a reaction by the reaction's reactionId value

## Bonus: +10 Points
* Application deletes a user's associated thoughts when the user is deleted.

## Built With
* HTML
* CSS
* BootStrap
* Javascript
* Node.js
* Nodemon
* Inquirer
* Express.js
* MongoDB
* Mongoose

## Installation and Setup
* Clone this repo
* Install Node
* Install Nodemon
* Install Express
* Install MongoDB
* Install Mongoose

## Website Link

## Github Repository
https://github.com/GordonOrr/FoundAmoeba

## Video Demonstration


## Screen Shots of Application
![Screen Shot One](./public/assets/images/screenshot-one.png?raw=true "Screenshot One")
![Screen Shot Two](./public/assets/images/screenshot-two.png?raw=true "Screenshot Two")

## Contribution
Made with ❤️ by Gordon Orr
