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
- in /src/rotuer/index.js import the newly created vue file and add it as a component in the routes array 
**NOTE: the path should be the same as the link from the homeButtons/index.js file**
- under the store folder, create a new folder and name it the same as the module
- create an index.js file for it. (this is the store module for vuex. You can use the exampleStore/index.js as a template)
- navigate to /src/store/index.js and import the newly created index file and add it to the modules
- in the same index file in the mutations: **openCurrentIndex** function add an if check for the new module 
```javascript
    // make sure to change the your button name to what you put as the 
    //button title in the homeButtons/index.js file 
    //also make sure to change the yourImportedModuleName to the correct imported module
     if (window.localStorage.getItem("name") == "Your Button Name") {
        state.currentIndexTitles.push(state.YourImportedModuleName.slideNames);
        state.totalNumberOfSlides = state.currentIndexTitles[0].length;
        return;
      }
```
# Adding Content for the Module
Your Module should follow the same structure as the testView.vue folder.
- Make sure to change the template header to the button title 
- add html in the slides. Follow this structure if you want:
```html
      <h2 class="panelTitle">Welcome to Introduction Financials</h2>
        <div class="wrapper">
           
          <div class="text">
            <p class="panelText">
              This training course will introduce you to the process, coordination, and information
              required to understand the Financials process in GFEBS.
            </p>
          </div>
          <div class="image">
            <img src="../../../../../img/GFEBS.jpeg" name="GFEBS" />
          </div>
        </div>
```
if you dont want to that is fine. We import the styles and you can change them however you want to make it look like the modlue you are copying
- FBPA class brings the text down to 10px
- bold class makes the text bold
- underline class makes the text underline 
---
- if you get to the section where the module has terms the user needs to click use this inside of the slide that needs it:

```html
    <h2 class="panelTitle">Perform Valuation on Foreign Currency</h2>
    <div class="wrapper">
        <div class="text">
            <p class="panelText">
                Here are a number key terms and concepts related to this section.
            <br/>
            <span class="bold">Click</span> each term to the right to learn more.
                <div class="baseTerm">
                <BaseTermButton :id="1" name="At the End of Each Period" />
                
                <BaseTermButton  :id="2" name="Performing a Valuation" />
            </div>
            <div class="termContain">
                <SlideContainer v-model:activeSlideId="this.$store.getters.getActiveTermId">
                    <Slide slideId="1">
                        <div class="slotContain">
                        <span class="baseTermTitle">
                            At the End of Each Period
                        </span>
                            <br/>
                        <p>
                            
                        </p>
                        </div>
                    </Slide>
                    <Slide slideId="2">
                    <div class="slotContain">
                        <span class="baseTermTitle">
                            Performing a Valuation
                        </span>
                            <br/>
                        <p>
                            
                        </p>
                        </div>
                    </Slide>   
                </SlideContainer>
            </div>
            </p>
        </div>
    </div>
```
- The base term button is what you use and it controls the slidecontainer inside the current slide. Make sure to name the term what the button title inside the module is named
```html
    <BaseTermButton :id="1" name="The Term name" />
```
---
When you get to the part of the module that requires the user to answer questions use this: 

```html
   <h2 class="panelTitle">Question 3</h2>
    <div class="wrapper">
        <div class="text">
          
          <div>
            <p class="panelText">
            GFEBS enables efficient and accurate financial management of the Army by:
                  <BaseQuestion :value="false" :id="'q31'" :labelName="'Centralizing Master Data'" :name="'q3'" />
                  <BaseQuestion :value="false" :id="'q32'" :labelName="'Standardizing Financial Management'" :name="'q3'" />
                  <BaseQuestion :value="false" :id="'q33'" :labelName="'Expediting the Period-End and Year-End Close processes'" :name="'q3'" />
                  <BaseQuestion :value="true" :id="'q34'" :labelName="'All of the above'" :name="'q3'" />
            </p>
          </div>
        </div>
        <div class="image">
            <BaseQuestionImage />
        </div>
    </div>

```

- the div with the BaseQuestionImage shouldnt be changed.
- the text above the BaseQuestions, is the actual question
- the value is either true or false. (true being correct and false incorrect)
- the id is question number and what ever question it is (IE: q for question and 3 because its question 3. the other number is what number the question answer is. So together q31 is question number 3 answer number 1)
- the label name is the actual answer text
- the name should be whatever question they are on ( IE: q3, question number 3)



