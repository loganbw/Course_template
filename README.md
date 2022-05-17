# Course Assessment Template
use this template to update the legacy GFEBS courses
- **NOTE: this template may be updated later to a new GUI** 
--- 
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
- Create a new view file in the views folder and name it the module name and view (moduleNameView.vue) **look at testView.vue for layout example**
- in /src/rotuer/index.js import the newly created vue file and add it as a component in the routes array **NOTE: the path should be the same as the link from the homeButtons/index.js file**
- under the store folder, create a new folder and name it the same as the module
- create an index.js file for it. (this is the store module for vuex. You can use the exampleStore/index.js as a template)
- navigate to /src/store/index.js and import the newly created index file and add it to the modules
- in the same index file in the mutations: **openCurrentIndex** function add an if check for the new module 
```javascript
    // make sure to change the your button name to what you put as the button title in the homeButtons/index.js file 
    //also make sure to change the yourImportedModuleName to the correct imported module
     if (window.localStorage.getItem("name") == "Your Button Name") {
        state.currentIndexTitles.push(state.YourImportedModuleName.slideNames);
        state.totalNumberOfSlides = state.currentIndexTitles[0].length;
        return;
      }
```
# Adding Content for the Module




