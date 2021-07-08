# When should you run the kickoff ot project REACT?
![CSFCSA](https://content.codecademy.com/courses/React/react_setup-039-app-js.png)

1. Ideally, the kickoff meeting should happen before teams and collaborators start a project as it helps set shared expectations.

2. Half a day is the minimum time required. This allows three to four hours in which to talk through the project goals, discovery tasks and research, ask questions, clarify client/team requests, and challenge assumptions. If blocking out an entire morning or afternoon isn’t feasible, divide it into two two-hour meetings, with set topics of discussion for each.

## Who needs to be involved?
> Getting the right people in a room at the same time will make life much easier down the line. Be sure to invite all stakeholders and collaborators.

>? It’ll give everyone a chance to meet each other, share their hopes for the project and highlight any potential differences in objectives and priorities. It’ll also help to establish a hierarchy of decision makers, which in turn will reduce the risk of scope creep.

### Attendees should include:

- An effective facilitator to head up and lead the discovery phase
- All key members of the creative team that will be involved in the project
- A representative from each relevant area of the business involved
- Any key stakeholders and decision makers
- If it’s not feasible to get everyone together at the same time, it’s still worth getting as many people apossible, then arrange follow-up interviews with those who were absent. Everybody needs to be on board and fee part of the team.

### Why is it important to run a kickoff?
> Kickoff and discovery shouldn’t just be a box-ticking exercise. When planned and conducted effectively it can be some of the most valuable time a team will spend together throughout the project lifespan. Discovery:

1. Give projects the best chance of succeeding, as they’re chance to iron out plans with the very individuals that will determine its success.
2. Help set accurate timelines, deadlines, and budgets.
3. Offer project collaborators the space to explain why things take as long as they do or why they need certain portions of the budget.
4. Uncover what clients/the team think of ideas and offers the chance to work together to create a vision everyone is happy with.
5. Help to consolidate ideas into one shared objective.
6. Allow plans to be agreed as a group and establish individual responsibilities, deadlines and workflow processes.



### What should you do before the discovery phase?
- It’s very important to set expectations for the kickoff and discovery phase in advance. Tell all attendees why they are being brought together (i.e. to get as much information as possible about the audience, project aims, required content, logistics, roles etc. and to formalize plans).

### In advance of the session:

> Pick a date, time, and location, then invite all those who need to be involved (use organization charts to see who heads up specific business sections, if unsure).

### Re-read and print out the branding guidelines for attendees to reference.
***Print out a list of what the team can offer in terms of site development, as well as some handy examples of previous project collateral (e.g. URLs or screenshots of previous website projects to demonstrate the team’s capabilities).***

***Print out screenshots of the website being (re)designed, so that attendees can see how the website looks currently and work out what needs to change, stay, and go.***

> Carry out some competitor research, by location and by service if necessary, to show an understanding of the relevant market.
> Share a proposed agenda for the kickoff so people can prepare themselves for the topics that will be covered.

### What should be included in the agenda?
> In her book, Collaborate: Bring people together around digital projects, Ellen de Vries states that a kickoff and discovery phase might include:

1. Taking stock of what already exists.
2. Looking at areas of potential for the project.
3. Establishing a shared language for the group, including roles and tasks.
4. Giving shape to a project and defining the tasks ahead of you.
5. Becky Taylor at GatherContent suggests that the agenda for website discovery sessions should be divided into four parts.



### A summary of everything discussed
1. Any outcomes, actions, and deliverables that were agreed
2. Anything that still needs a decision to be made about it
3. The business goals and website goals that you clarified
4. The target audience the new website will aim for
5. Any notes on the plan of action, even if they are only brief
6. Dissemination and communication after the session are important to make sure things are actioned and followed up. The kickoff and discovery is just the beginning, with plenty more collaboration and challenges to come, but it will set teams off on the right course and give their website projects the best chance of success.





-------------------------------------------------------------------------------------------------------------------





1. Creating a New Project with Create React App
> In this step, you’ll create a new application using the npm package manager to run a remote script. The script will copy the necessary files into a new directory and install all dependencies.

- When you installed Node, you also installed a package managing application called npm. npm will install JavaScript packages in your project and also keep track of details about the project. If you’d like to learn more about npm, take a look at our How To Use Node.js Modules with npm and package.json tutorial.

- npm also includes a tool called npx, which will run executable packages. What that means is you will run the Create React App code without first downloading the project.

- The executable package will run the installation of create-react-app into the directory that you specify. It will start by making a new project in a directory, which in this tutorial will be called digital-ocean-tutorial. Again, this directory does not need to exist beforehand; the executable package will create it for you. The script will also run npm install inside the project directory, which will download any additional dependencies.

- To install the base project, run the following command:

1. npx create-react-app 
 
> This command will kick off a build process that will download the base code along with a number of dependencies.

* When the script finishes you will see a success message that says:

> Output
```
Success! Created digital-ocean-tutorial at your_file_path/digital-ocean-tutorial
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd digital-ocean-tutorial
  npm start
```  
### Happy hacking!
> your_file_path will be your current path. If you are a macOS user, it will be something like /Users/your_username; if you are on an Ubuntu server, it will say something like /home/your_username.

> You will also see a list of npm commands that will allow you to run, build, start, and test your application. You’ll explore these more in the next section.

***Note: There is another package manager for JavaScript called yarn. It’s supported by Facebook and does many of the same things as npm. Originally, yarn provided new functionality such as lock files, but now these are implemented in npm as well. yarn also includes a few other features such as offline caching. Further differences can be found on the yarn documentation.***

***If you have previously installed yarn on your system, you will see a list of yarn commands such as yarn start that work the same as npm commands. You can run npm commands even if you have yarn installed. If you prefer yarn, just replace npm with yarn in any future commands. The results will be the same.***

1. Now your project is set up in a new directory. Change into the new directory:


 
> You are now inside the root of your project. At this point, you’ve created a new project and added all of the 
node_modules/ contains all of the external JavaScript libraries used by the application. You will rarely need to open it.
> The public/ directory contains some base HTML, JSON, and image files. These are the roots of your project. You’ll have an opportunity to explore them more in Step 4.
The src/ directory contains the React JavaScript code for your project. Most of the work you do will be in that directory. You’ll explore this directory in detail in Step 5.

- The .gitignore file contains some default directories and files that git—your source control—will ignore, such as the node_modules directory. The ignored items tend to be larger directories or log files that you would not need in source control. It also will include some directories that you’ll create with some of the React scripts.
README.md is a markdown file that contains a lot of useful information about Create React App, such as a summary of commands and links to advanced configuration. For now, it’s best to leave the README.md file as you see it. As your project progresses, you will replace the default information with more detailed information about your project.
- The last two files are used by your package manager. When you ran the initial npx command, you created the base project, but you also installed the additional dependencies. When you installed the dependencies, you created a package-lock.json file. This file is used by npm to ensure that the packages match exact versions. This way if someone else installs your project, you can ensure they have identical dependencies. Since this file is created automatically, you will rarely edit this file directly.

- The last file is a package.json. This contains metadata about your project, such as the title, version number, and dependencies. It also contains scripts that you can use to run your project.

- Open the package.json file in your favorite text editor:

### nano package.json
 
- When you open the file, you will see a JSON object containing all the metadata. If you look at the scripts object, you’ll find four different scripts: start, build, test, and eject.

- These scripts are listed in order of importance. The first script starts the local development environment; you’ll get to that in the next step. The second script will build your project. You’ll explore this in detail in Step 4, but it’s worth running now to see what happens.

- The build Script
To run any npm script, you just need to type npm run script_name in your terminal. There are a few special scripts where you can omit the run part of the command, but it’s always fine to run the full command. To run the build script, type the following in your terminal:

### npm run build
 
 
 ## You will immediately see the following message:




### serve -s build

### Find out more about deployment here:

  > bit.ly/NETFLIEY
List out the project contents and you will see some new directories:


```
ls -a
 
Output
build/
node_modules/
public/
src/
.gitignore
README.md
package-lock.json
package.json

```

- You now have a build directory. If you opened the .gitignore file, you may have noticed that the build directory is ignored by git. That’s because the build directory is just a minified and optimized version of the other files. There’s no need to use version control since you can always run the build command. You’ll explore the output more later; for now, it’s time to move on to the test script.

- The test Script
The test script is one of those special scripts that doesn’t require the run keyword, but works even if you include it. This script will start up a test runner called Jest. The test runner looks through your project for any files with a .spec.js or .test.js extension, then runs those files.

- To run the test script, type the following command:

- npm test
 
### After running this script your terminal will have the output of the test suite and the terminal prompt will disappear. It will look something like this:
```
Output
 PASS  src/App.test.js
  ✓ renders learn react link (67ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        4.204s
Ran all test suites.

Watch Usage
 › Press f to run only failed tests.
 › Press o to only run tests related to changed files.
 › Press q to quit watch mode.
 › Press p to filter by a filename regex pattern.
 › Press t to filter by a test name regex pattern.
 › Press Enter to trigger a test run.

```


1. There are a few things to notice here. First, as noted before, it automatically detects any files with test extensions including .test.js and .spec.js. In this case, there is only one test suite—that is, only one file with a .test.js extension—and that test suite contains only one test. Jest can detect tests in your code hierarchy, so you can nest tests in a directory and Jest will find them.

2.  Jest doesn’t run your test suite once and then exit. Rather, it continues running in the terminal. If you make any changes in the source code, it will rerun the tests again.

3. You can also limit which tests you run by using one of the keyboard options. If you type o, for example, you will only run the tests on files that have changed. This can save you lots of time as your test suites grow.

4. Finally, you can exit the test runner by typing q. Do this now to regain your command prompt.

### The eject Script
- The final script is npm eject. This script copies your dependencies and configuration files into your project, giving you full control over your code but ejecting the project from the Create React App integrated toolchain. You will not run this now because, once you run this script, you can’t undo this action and you will lose any future Create React App updates.

- The value in Create React App is that you don’t have to worry about a significant amount of configuration. Building modern JavaScript applications requires a lot of tooling from build systems, such as Webpack, to compilation tools, such as Babel. Create React App handles all the configuration for you, so ejecting means dealing with this complexity yourself.

- The downside of Create React App is that you won’t be able to fully customize the project. For most projects that’s not a problem, but if you ever want to take control of all aspects of the build process, you’ll need to eject the code. However, as mentioned before, once you eject the code you will not be able to update to new versions of Create React App, and you’ll have to manually add any enhancements on your own.

- At this point, you’ve executed scripts to build and test your code. In the next step, you’ll start the project on a live server.

## Step 3 — Starting the Server
> In this step, you will initialize a local server and run the project in your browser.

1. You start your project with another npm script. Like npm test, this script does not need the run command. When you run the script you will start a local server, execute the project code, start a watcher that listens for code changes, and open the project in a web browser.

2. Start the project by typing the following command in the root of your project. For this tutorial, the root of your project is the digital-ocean-tutorial directory. Be sure to open this in a separate terminal or tab, because this script will continue running as long as you allow it:

### npm start
 
***You’ll see some placeholder text for a brief moment before the server starts up, giving this output:***
```
Output
Compiled successfully!

You can now view digital-ocean-tutorial in the browser.

  http://localhost:3000
```

***Note that the development build is not optimized.***
1. To create a production build, use npm run build.
> If you are running the script locally, it will open the project in your browser window and shift the focus from the terminal to the browser.

> If that doesn’t happen, you can visit http://localhost:3000/ to see the site in action. If you already happen to have another server running on port 3000, that’s fine. Create React App will detect the next available port and run the server with that. In other words, if you already have one project running on port 3000, this new project will start on port 3001.

> If you are running this from a remote server you can still see your site without any additional configuration. The address will be http://your_server_ip:3000. If you have a firewall configured, you’ll need to open up the port on your remote server.

> In the browser, you will see the following React template project:

## React template project

***As long as the script is running, you will have an active local server. To stop the script, either close the terminal window or tab or type CTRL+C or ⌘-+c in the terminal window or tab that is running your script.***

> At this point, you have started the server and are running your first React code. But before you make any changes to the React JavaScript code, you will see how React renders to the page in the first place.

### Step 4 — Modifying the Homepage
> In this step, you will modify code in the public/ directory. The public directory contains your base HTML page. This is the page that will serve as the root to your project. You will rarely edit this directory in the future, but it is the base from which the project starts and a crucial part of a React project.

1. If you cancelled your server, go ahead and restart it with npm start, then open public/ in your favorite text editor in a new terminal window:
```
nano public/
 
Alternatively, you can list the files with the ls command:

ls public/
 
You will see a list of files such as this:

Output
favicon.ico
logo192.png
manifest.json
index.html
logo512.png
robots.txt
```

1. favicon.ico, logo192.png, and logo512.png are icons that a user would see either in the tab of their browser or on their phone. The browser will select the proper-sized icons. Eventually, you’ll want to replace these with icons that are more suited to your project. For now, you can leave them alone.

2. The manifest.json is a structured set of metadata that describes your project. Among other things, it lists which icon will be used for different size options.

3. The robots.txt file is information for web crawlers. It tells crawlers which pages they are or are not allowed to index. You will not need to change either file unless there is a compelling reason to do so. For instance, if you wanted to give some users a URL to special content that you do not want easily accessible, you can add it to robots.txt and it will still be publicly available, but not indexed by search engines.

4. The index.html file is the root of your application. This is the file the server reads, and it is the file that your browser will display. Open it up in your text editor and take a look.


5. The file is pretty short. There are no images or words in the <body>. That’s because React builds the entire HTML structure itself and injects it with JavaScript. But React needs to know where to inject the code, and that’s the role of index.html.



 
6. Save and exit your text editor. Check your browser. The title is the name located on the browser tab. It will update automatically. If not, refresh the page and notice the change.

7. Now go back to your text editor. Every React project starts from a root element. There can be multiple root elements on a page, but there needs to be at least one. This is how React knows where to put the generated HTML code. Find the element <div id="root">. This is the div that React will use for all future updates. Change the id from root to base:


### public/index.html
<!-- <!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    ...
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="base"></div>
    <!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->

### Save the changes.

***You will see an error in your browser:***


 
***Save and exit index.html.***



## Step 5 — Modifying the Heading Tag and Styling
In this step, you will make your first change to a React component in the src/ directory. You’ll make a small change to the CSS and the JavaScript code that will automatically update in your browser using the built-in hot reloading.

#### If you stopped the server, be sure to restart it with npm start. Now, take some time to see the parts of the src/ directory. You can either open the full directory in your favorite text editor, or you can list out the project in a terminal with the following command:

ls src/
 
You will see the following files in your terminal or text editor.
```
Output
App.css
App.js
App.test.js
index.css
index.js
logo.svg
serviceWorker.js
setupTests.js
Let’s go through these files one at a time.
```
### You will not spend much time with the serviceWorker.js file at first, but it can be important as you start to make progressive web applications. The service worker can do many things including push notifications and offline caching, but for now it’s best to leave it alone.


```
Open App.test.js:

nano src/App.test.js
 
When you open it, you’ll see a basic test:

digital-ocean-tutorial/src/App.test.js
import React from 'react';
import { render } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  const { getByText } = render(<App />);
  const linkElement = getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```


- The test is looking for the phrase learn react to be in the document. If you go back to the browser running your project, you’ll see the phrase on the page. React testing is different from most unit tests. Since components can include visual information, such as markup, along with logic for manipulating data, traditional unit tests do not work as easily. React testing is closer to a form of functional or integration testing.

- Next, you’ll see some styling files: App.css, index.css, and logo.svg. There are multiple ways of working with styling in React, but the easiest is to write plain CSS since that requires no additional configuration.

- There are multiple CSS files because you can import the styles into a component just like they were another JavaScript file. Since you have the power to import CSS directly into a component, you might as well split the CSS to only apply to an individual component. What you are doing is separating concerns. You are not keeping all the CSS separate from the JavaScript. Instead you are keeping all the related CSS, JavaScript, markup, and images grouped together.

1. Open App.css in your text editor. If you are working from the command line, you can open it with the following command:
```
nano src/App.css
 
This is the code you’ll see:

digital-ocean-tutorial/src/App.css
.App {
  text-align: center;
}

.App-logo {
  height: 40vmin;
  pointer-events: none;
}

@media (prefers-reduced-motion: no-preference) {
  .App-logo {
    animation: App-logo-spin infinite 20s linear;
  }
}

.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

.App-link {
  color: #61dafb;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

- This is a standard CSS file with no special CSS preprocessors. You can add them later if you want, but at first, you only have plain CSS. Create React App tries to be unopinionated while still giving an out-of-the-box environment.

- Back to App.css, one of the benefits of using Create React App is that it watches all files, so if you make a change, you’ll see it in your browser without reloading.

- To see this in action make a small change to the background-color in App.css. Change it from #282c34 to blue then save the file. The final style will look like this:
```
digital-ocean-tutorial/src/App.css
.App {
  text-align: center;
}
...
.App-header {
  background-color: blue
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}
...

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

1. Check out your browser. Here’s how it looked before:

2. React app with dark background
![SDFDSD](https://yagrawal.dev/opt/build/repo/content/images/34bbc376a2719dcdc9a1d72ddfce9594/basic_create_react_app.gif)


P- Here’s how it will look after the change:

- React app with blue background

- Go ahead and change background-color back to #282c34.

```
.App {
  text-align: center;

...

.App-header {
  background-color: #282c34
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

...

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```
#### Save and exit the file.

***You’ve made a small CSS change. Now it’s time to make changes to the React JavaScript code. Start by opening index.js.***

```
nano src/index.js
 
Here’s what you’ll see:

digital-ocean-tutorial/src/index.js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';







ReactDOM.render(<App />, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```
![SSAFSAF](https://www.christophermallory.com/wp-content/uploads/2018/01/mongodb.png)

1. At the top, you are importing React, ReactDOM, index.css, App, and serviceWorker. By importing React, you are actually pulling in code to convert JSX to JavaScript. JSX are the HTML-like elements. For example, notice how when you use App, you treat it like an HTML element <App />. You’ll explore this more in future tutorials in this series.

2. ReactDOM is the code that connects your React code to the base elements, like the index.html page you saw in public/. Look at the following highlighted line:

```
digital-ocean-tutorial/src/index.js
...
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));
...
serviceWorker.unregister();
```

3. This code instructs React to find an element with an id of root and inject the React code there. <App/> is your root element, and everything will branch from there. This is the beginning point for all future React code.

4. At the top of the file, you’ll see a few imports. You import index.css, but don’t actually do anything with it. By importing it, you are telling Webpack via the React scripts to include that CSS code in the final compiled bundle. If you don’t import it, it won’t show up.
```
Exit from src/index.js.

At this point, you still haven’t seen anything that you are viewing in your browser. To see this, open up App.js:

nano src/App.js
 
The code in this file will look like a series of regular HTML elements. Here’s what you’ll see:

digital-ocean-tutorial/src/App.js
import React from 'react';
import logo from './logo.svg';
import './App.css';

<!-- function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
} -->

export default App;
```

5. Change the contents of the <p> tag from Edit <code>src/App.js</code> and save to reload. to Hello, world and save your changes.
```
digital-ocean-tutorial/src/App.js
...

function App() {
  return (
    <!-- <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
            Hello, world
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"

```


6. Head over to your browser and you’ll see the change:

7. React app with "Hello, world" in paragraph tag

***You’ve now made your first update to a React component.***

* Before you go, notice a few more things. In this component, you import the logo.svg file and assign it to a variable. Then in the <img> element, you add that code as the src.

* There are a few things going on here. Look at the img element:
```
digital-ocean-tutorial/src/App.js

<!-- function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
            Hello, world
        </p>
 -->
 
``` 
- Notice how you pass the logo into curly braces. Anytime you are passing attributes that are not strings or numbers, you need to use the curly braces. React will treat those as JavaScript instead of strings. In this case, you are not actually importing the image; instead you are referencing the image. When Webpack builds the project it will handle the image and set the source to the appropriate place.

- Exit the text editor.

- If you look at the DOM elements in your browser, you’ll see it adds a path. If you are using Chrome, you can inspect the element by right-clicking the element and selecting Inspect.

- Here’s how it would look in the browser:

- Inspecting element with chrome dev tools

- The DOM has this line:
```
<img src="/static/media/logo.5d5d9eef.svg" class="App-logo" alt="logo">
```

### Your code will be slightly different since the logo will have a different name. Webpack wants to make sure the image path is unique. So even if you import images with the same name, they will be saved with different paths.

### At this point, you’ve made a small change to the React JavaScript code. In the next step, you’ll use the build command to minify the code into a small file that can be deployed to a server.

## Step 6 — Building the Project
1. In this step, you will build the code into a bundle that can be deployed to external servers.

2. Head back to your terminal and build the project. You ran this command before, but as a reminder, this command will execute the build script. It will create a new directory with the combined and minified files. To execute the build, run the following command from the root of your project:

**npm run build**
 
3. There will be a delay as the code compiles and when it’s finished, you’ll have a new directory called build/.

4. Open up build/index.html in a text editor.
```
build/index.html
``` 


 
### The build directory takes all of your code and compiles and minifies it into the smallest usable state. It doesn’t matter if a human can read it, since this is not a public-facing piece of code. Minifying like this will make the code take up less space while still allowing it to work. Unlike some languages like Python, the whitespace doesn’t change how the computer interprets the code.

## Conclusion
> **In this tutorial, you have created your first React application, configuring your project using JavaScript build tools without needing to go into the technical details. That’s the value in Create React App: you don’t need to know everything to get started. It allows you to ignore the complicated build steps so you can focus exclusively on the React code.**

**You’ve learned the commands to start, test, and build a project. You’ll use these commands regularly, so take note for future tutorials. Most importantly, you updated your first React component.**

***If you would like to see React in action, try our How To Display Data from the DigitalOcean API with React tutorial.***
