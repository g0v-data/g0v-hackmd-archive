# How to Add Fireworks Effect to your React App

This React app guide will teach you how to integrate fireworks effects into it. We will start by explaining how to set up a new React project. And then we will learn how to incorporate a firework effect library and customize it to make user engagement more captivating and interactive.

Add fireworks to your web applications to celebrate special events, and interactive games and enhance your user interface with excitement. After reading this short guide, you have sufficient knowledge and skills that can make you able to implement them on your React projects.

## Prerequisites
Before you learn to use Firework Effects in a React app, you must understand React and JS basics. To go through this lesson about building and customizing components, one should be aware of React components, state management, and props. Moreover, it would be helpful if you knew how to code in new JavaScript standards (ES6+) so that it would be easy for you to understand examples and changes made throughout the text.

Establishing a React development environment is another essential requirement; it means that Node.js and npm(Node Package Manager) should be in the machine as well. While these are basic tools used to manage dependencies and work with React apps generally, installing Node.js (that also brings npm as a bonus) offered on their website would be necessary if not done already.

After installing Node.js and npm, you will need to configure your React environment by working with Create React App for beginning development. Set up a new React project that follows some common structure and lets you build customer modules It simplifies the initial setup process, allowing you to focus on building your application without worrying about configuration details.

Once you have a basic knowledge of React and JavaScript, as well as an appropriate development environment, you will be ready to follow this guide to successfully integrate firework effects to React application.

## Setting Up the React Project
In the section, your reading will guide you through the initial phases of setting up a React project with fireworks that will be eventually integrated. These involve creating a new React application through the Create React App method as well as installing packages that are required .

We will begin with Create React App, a commonly used tool, it helps to establish new React projects in a standardized manner by providing structure and configuration that are standard, thereby easing setup at the start. Go ahead, and follow these steps.

### Running npx create-react-app firework-app
Open your terminal and run the following command:

```bash
npx create-react-app firework-app
```
If you run this command line, you can start your React project in the `firework-app` folder straight away. It is possible because `npx` is bundled with `npm` starting from version 5.2 and so it enables you to execute commands without having them installed globally on your machine.

### Navigating to the Project Directory
After you have finished setting up the system, you need to navigate to the new project directory by typing:
```bash
cd firework-app
```
At this moment you are inside the project directory where you can start developing your application.

### Installing Required Dependencies
Afterward, to present fireworks effects, we have to put another library. It is easier to use and customize than other libraries that are available but not used in this guide like `fireworks-js` and has most tutorials about it. We chose to use `fireworks-js` library for this tutorial because of its simplicity and flexibility. You have the possibility of making different firework effects with parameters that can be changed as you wish with the help of this particular tool.

You should install `fireworks-js` by entering the following text within your command-line interface (CLI):
```bash
npm install fireworks-js
```
In case yarn is your favorite, you may want to utilize this command:

```bash
yarn add fireworks-js
```
You can make `fireworks-js` available for your React components by adding this command to your project’s dependencies.

## Integrating Firework Effects
We have set up the React project for you and installed all the dependencies so the next thing will be creating fireworks within your app for you to do this you must first import the Firework library, create a Firework component specific to its use with your application then finally render it within the main application.

### Importing the Firework Library into the React App
Initial stage is when we must bring the `fireworks-js` library to our React application. When you are planning on using firework effects, like in `App.js` or a new component file, open up the file then write down this import statement at the beginning:

```javascript
import Fireworks from 'fireworks-js';
```
By stating the above, `fireworks-js` is available to be used in your component.

### Creating a Firework Component
After that, we might create a Firework Component, the main job of which would be to decide on the way fireworks will be displayed. This one should take care of launching and painting the fireworks animation.

Create a new file called Firework.js in your project's src folder. In this file, create a functional React component using the following format:

```javascript
import React, { useEffect, useRef } from 'react';
import Fireworks from 'fireworks-js';

const Firework = () => {
  const containerRef = useRef(null);

  useEffect(() => {
    const container = containerRef.current;
    const options = {
      rocketsPoint: 50,
      hue: { min: 0, max: 360 },
      delay: { min: 15, max: 30 },
      speed: 2,
      acceleration: 1.05,
      friction: 0.98,
      gravity: 1.5,
      particles: 50,
      trace: 3,
      explosion: 5,
      autoresize: true,
      brightness: { min: 50, max: 80 },
      decay: { min: 0.015, max: 0.03 },
      mouse: { click: false, move: false, max: 1 },
      boundaries: { x: 50, y: 50, width: container.clientWidth, height: container.clientHeight },
      sound: { enable: false },
    };
    const fireworks = new Fireworks(container, options);
    fireworks.start();

    return () => {
      fireworks.stop();
    };
  }, []);

  return <div ref={containerRef} style={{ width: '100vw', height: '100vh' }} />;
};

export default Firework;
```
We use the `useRef` hook in this component to get a reference to the containing `div`, that will be showing the firework effects. When this component is unmounted, the `useEffect` hook is employed to clear out the firework animation upon mounting and dismounting it.

### Adding the Firework Effect Logic Using the Imported Library
Inside the `useEffect` hook, the Fireworks instance is initialized using both the reference to the container and defined options for firework effects. We ensure that an animation demonstrating fireworks will halt if the component gets removed by use of the `useEffect` hook by returning a cleanup function.

### Rendering the Firework Component in the Main Application
To make the fireworks go off, you must include the fireworks component in our primary app. Locate `App.js` file and import the Firework component as the first thing in it:

```javascript
import Firework from './Firework';
```
Then add Firework component to the JSX that is returned by `App` component:

```javascript
function App() {
  return (
    <div className="App">
      <Firework />
    </div>
  );
}

export default App;
```
Kindly, execute your React application utilizing the command that follows:
```bash
npm start
```
You can know that the integration was successful by observing that the firework effects have been displayed on the screen after you open your browser and reach `http://localhost:3000`. Here is the output:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f81e256cce80aa6ce4c50f6e6a883f8.gif)



You can now find the fireworks effect in your React application by following these steps. 

## Conclusion
We have  explained how to include and personalize fireworks effects within a React app. First of all, we set up a new project that will use Create-`React-App` and loaded a `fireworks-js` library. So, we installed our fireworks, and added those cool animations or whatever else you like best – look at them now!

With this short guide, you are capable of developing firework effects on your React applications to form interesting user experiences. Whenever you are commemorating special occasions, incorporating engaging parts, or just increasing the attractiveness of your undertaking for eyes these fireworks make your interface look much better. Thank you and happy coding!