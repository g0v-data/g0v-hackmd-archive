# How to Create a Fireworks Effect on Your React App

This [React](https://react.dev/) app guide will teach you how to integrate fireworks effects into it. We will start by stating the importance of the fireworks effect on your website and the categories of websites on which you should and should not use the fireworks effect. Then we will move on to the main subject of the article, which involves the creation of the fireworks effect, which starts  by explaining how to set up a new React project. And then we will learn how to incorporate a firework effect library to create the fireworks effect in the React application.

Add fireworks to your web applications to celebrate special events and interactive games and enhance your user interface with excitement. After reading this short guide, you will have sufficient knowledge and skills to implement them in your React projects.

## The Usefulness of Adding Fireworks to Your Website
Incorporating firework effects into your website can significantly enhance the user experience by adding a layer of visual excitement and engagement. Fireworks are often associated with celebration and joy, making them an excellent tool for marking special occasions, achievements, or milestones within your application. This can create a memorable experience for your users, making your site stand out.

It is equally possible to improve user interaction and satisfaction by adding fireworks. Firework effects like using buttons or filling out forms could transform an ordinary procedure into an enjoyable one due to its interactivity. It can encourage more usage of your site by luring users to keep coming back, thus increasing retention and time spent on your platform.

For important events or notifications, fireworks can serve as a powerful visual cue. For example, in a gaming application, you can use fireworks to celebrate level-ups or other big wins, which will give instant feedback that feels good to the player. In e-commerce, fireworks can be used to indicate that a person has made a successful purchase or that they have received a special offer, thus improving their overall shopping experience.

In addition, the aesthetic appeal of your website can be enhanced through fireworks’ effects. A tastefully arranged fireworks exhibition can add to the theme and branding of your site, thus resulting in a consistent design that is visually appealing. It is a way of improving the general attitude of site visitors towards it, therefore giving it a more refined and professional appearance.

Above all, incorporating modern technology like firework displays on your website does not entail just an addition of some color or images but enabling its visitors to have an interesting, participatory, and unforgettable encounter such that they will be able to differentiate it from other websites. To come up with a site that has fireworks that are emotionally engaging and visually enticing, an environment that is vibrant and pleasurable to be in is crucial to be developed for clients as well.

## Websites Where You Should Use Firework Effects
If applied, fireworks effects can greatly improve a user’s enjoyment of some websites. Below are some  appropriate websites where fireworks effects can be used:

Websites that celebrate special events or are used for isolated events such as New Year’s Eve, Independence Day, or similar celebrations can easily use fireworks to enhance the celebratory mood. The fireworks visualization increases the celebratory element and makes the event more involving for the visiting audience.

On electronic trading platforms, fireworks can make special offers, flash sales, and show successful operations. One case in point is when a customer completes an order other than during seasonal discounts like Black Friday. They attract much more fun as well as more involved customers.

 Fireworks in gaming environments can be used for various purposes, such as celebrating player achievements, leveling up, or victories. Instantaneous visual feedback creates a gratifying environment, thereby improving player satisfaction and retention.

 Fireworks can add excitement and interest to interactive, educational platforms aimed at children, especially when they celebrate milestones or give the right answers. All these can help children learn better and work harder at their tasks.

 Designers, artists, and other creatives sometimes use fireworks to show their work attractively and originally. For example, they can make the fireworks burst out whenever a user hovers over or clicks on a project page to instill a sense of surprise and fun.
 
## Websites Where You Should Not Use Firework Effects
Despite their capacity to hold users’ attention, the fireworks effect may not be appropriate on any website. Below are situations in which one should refrain from doing so:

Websites for professional services, businesses, legal firms, and financial institutions must be clean, formal, and focused; using fireworks may make users question your seriousness in the company, which could look ridiculous.

News websites, academic publications, or websites dedicated to distributing research in general should focus more on improving readability and accessibility. Users may not concentrate on the content because fireworks force their attention elsewhere.

Healthcare websites, patient services, or medical information should have a tranquil and calming design.  Fireworks can be inappropriate or inconsiderate in cases where individuals require sensitive data.

Simpler websites are designed with minimalism in mind, focusing on simplicity and a clear message. However, using fireworks on such pages may distract from their initial idea by making them look overloaded and unsystematic.

## Prerequisites
Before you learn to use Firework Effects in a React app, you must understand [React](https://react.dev/) and [JavaScript](https://www.javascript.com/) basics. To go through this lesson about building and customizing components, one should be aware of React components, state management, and props. Moreover, it would be helpful if you knew how to code in new JavaScript standards [(ES6+)](https://dev.to/cliff123tech/javascript-es6-features-13co) so that it would be easy for you to understand examples and changes made throughout the text.

Establishing a React development environment is another essential requirement; it means that [Node.js](https://nodejs.org/en) and [npm](https://www.npmjs.com/) (Node Package Manager) should be in the machine as well. While these are basic tools used to manage dependencies and work with React apps generally, installing Node.js (which also brings npm as a bonus) offered on their website would be necessary if not already done.

After installing Node.js and npm, you configure your React environment by working with `Create React App` to begin development. Set up a new React project that follows some common structure and lets you build customer modules. It simplifies the initial setup process, allowing you to focus on building your application without worrying about configuration details.

Once you have a basic knowledge of React and JavaScript, as well as an appropriate development environment, you will be ready to follow this guide to successfully integrate the Firework effect into the React application.

## Setting up the React Project
In this section, your reading will guide you through the initial phases of setting up a React project with fireworks that will be eventually integrated. These involve creating a new React application through the `Create React App` method as well as installing the packages that are required.

We will begin with the `Create React App`, a commonly used tool that helps establish new React projects in a standardized manner by providing structure and configuration that are standard, thereby easing setup at the start. Go ahead and follow these steps.

### Running npx create-react-app firework-app
Open your terminal and run the following command:

```bash
npx create-react-app firework-app
```
If you run this command, you can start your React project in the `firework-app` folder right away. It is possible because `npx` is bundled with `npm` starting from version 5.2, and so it enables you to execute commands without having them installed globally on your machine.

After you have finished setting up the system, you need to navigate to the new project directory by typing:
```bash
cd firework-app
```
At this moment, you are inside the project directory, where you can start developing your application.

### Installing the required dependencies
Afterward, to present fireworks effects, we have to add another library. It is easier to use and customize than other libraries that are available but not used in this guide, like [fireworks-js](https://fireworks.js.org/), and has most tutorials about it. We chose to use the `fireworks-js` library for this tutorial because of its simplicity and flexibility. You have the possibility of making different fireworks effects with parameters that can be changed as you wish with the help of this particular tool.

You should install `fireworks-js` by entering the following text within your command-line interface (CLI):

```bash
npm install fireworks-js
```
In case `yarn` is your favorite, you may want to utilize this command:

```bash
yarn add fireworks-js
```
You can make `fireworks-js` available for your React components by adding this command to your project’s dependencies.

## Integrating Firework Effects
We have set up the React project and installed all the dependencies, so the next thing will be creating fireworks within your app. For you to do this, you must first import the Firework library, create a Firework component specific to its use with your application, and finally render it within the main application. This section will show you how to go about it.

### Importing the Firework Library into the React App
The initial stage is when we must bring the `fireworks-js` library to our React application. When you are planning on using firework effects, like in `App.js` or a new component file, open up the file and write down this import statement at the beginning:

```javascript
import Fireworks from 'fireworks-js';
```
By stating the above, `fireworks-js` is available to be used in your component.

After that, we have to create a firework component, the main job of which would be to decide how fireworks will be displayed. This one should take care of launching and painting the fireworks animation.

Create a new file called Firework.js in your project's `src` folder. In this file, create a functional React component using the following format:

```javascript
import React, { useEffect, useRef } from "react";
import Fireworks from "fireworks-js";

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
      boundaries: {
        x: 50,
        y: 50,
        width: container.clientWidth,
        height: container.clientHeight,
      },
      sound: { enable: false },
    };
    const fireworks = new Fireworks(container, options);
    fireworks.start();

    return () => {
      fireworks.stop();
    };
  }, []);

  return <div ref={containerRef} style={{ width: "100vw", height: "100vh" }} />;
};

export default Firework;
```
There is a color JavaScript function named `Firework` in the above code block. The necessary React hooks (`useEffect` and `useRef`) and `Fireworks` library are imported into this function as required. Consequently, a reference `(containerRef)` was created using the `useRef` method inside this function. When the component mounts, a new `Fireworks` instance is created using the `useEffect` hook with specific options like rocket point, hue range, delay, and speed, among others. Fireworks will be shown in the `container` being referred to; the fireworks effect will stop when the component unmounts; the component gives back a division styled in such a way that it covers the entire viewport and serves as a `container` for fireworks display; in the end, the `Firework` component is exported as the default export.


### Adding the Firework Effect Logic Using the Imported Library
Inside the `useEffect` hook, the `Fireworks` instance is initialized using the reference to the `container` and defined options for firework effects. We ensure that an animation demonstrating fireworks will halt if the component gets removed by  the `useEffect` hook by returning a cleanup function.

To make the fireworks go off, you must include the `fireworks` component in our primary app. Locate the `App.js` file and import the Firework component as the first thing in it.

```javascript
import Firework from "./Firework";
```
The code snippet above imports `Firework` from the `Fireworks` directory, and is an import statement for a JavaScript `ES6` module. Instead of having to specify the path through which JavaScript should import a file within the same directory, developers can use a default import, which is contained in the same Firework directory `(./)`.

Next, add the Firework component to the [JSX](https://legacy.reactjs.org/docs/introducing-jsx.html) that is returned by the `App` component:

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

The code defines the `app` component as a React function. Inside that component, it gives back a `JSX` one, a `div` with the class name. Another component called `Firework` will be shown within this `div`. At last, the `App` component will be exported as a default object of this module. Being arranged this way means that the `App` component can be reused elsewhere in an application, whereas `Firework` might serve as a visual or logical part of the UI.

Kindly execute your React application utilizing the command that follows:
```bash
npm start
```
You can tell that the integration was successful by observing that the fireworks effects have been displayed on the screen after you open your browser and reach `http://localhost:3000`. 

Output:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f81e256cce80aa6ce4c50f6e6a883f8.gif)

With this, we have successfully created the fireworks effect on our React application. 

## A perfect example
[Google](https://www.google.com/) often adds firework animations to its [Google Doodles](https://doodles.google/) to mark important days, holidays, and events that matter. These doodles, which can be interacted with attractively, appear on the front page and involve people through graphic creativity and festivity. Holidays include the final day of the year celebrations, holidays for independence, and dates of critical events.

Reasons that can make sure animations are essential include capturing the attention of users, promoting engagement, and enlightening about cultural and historical information, to mention but a few. At once, they are establishing Google’s image as an innovative and global enterprise. In other words, the countdown clock with fireworks celebrated during New Year’s Eve 2020 as well as an interactive fireworks game that was provided by the Fourth of July 2019 doodle.

Fireworks doodles make the events more fun and relatable, and they recognize how Google is centered on creativity and user engagement. They mostly denote important landmarks like scientific breakthroughs or cultural festivals, injecting a fun and learning aspect into the user journey.

For Example:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e0f734317db539badba2d3379abffbd9.gif)
Source: Google.com

The GIF above explains the usefulness of the fireworks effect in an application. Here, Google uses this special effect to celebrate a team's victory in a football match. These effects promote a sense of comfort and interest whenever a user enters the site.


## Conclusion
With this short guide, you can create firework effects on your React applications to create interesting user experiences. Whenever you commemorate special occasions, incorporate engaging parts, or increase the attractiveness of your undertaking for the eyes, these fireworks make your interface look much better. 

Thank you, and happy coding!