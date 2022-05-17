# Course Assessment Template
use this template to update the legacy GFEBS courses
- NOTE: this template may be updated later to a new GUI 
# Getting Started
- clone this repository ( if git is still there rm -rf .git to remove it)
- git init and create a new repo for the new assessment
- npm i
- npm run dev to run test enviroment
# Adding the home page data 
- Add the header and note (the yellow text under the header) for the main assessment in the /src/layouts/WindowPortalHeader.vue file
- Change the text in /src/views/HomeView.vue to the  current assessment text ( this the text underneath the crest) 
- To add the main buttons navigate to /src/store/homeButtons/index.js
you can add the title of the button and the link to the module there
(make sure you add the link from the store index file to the router file /src/router/index.js)
# Creating the Module





