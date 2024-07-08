# How to Add Fireworks Effect to your React App

This [React](https://react.dev/) app guide will teach you how to integrate fireworks effects into it. We will start by stating the importance of the fireworks effect on your website, and categories of websites you should and should not use the fireworks effect Then we will move on to the main subject of the article which involves the creation of the fireworks effect which starts  by explaining how to set up a new React project. And then we will learn how to incorporate a firework effect library to create the fireworks effect on the react application.

Add fireworks to your web applications to celebrate special events, and interactive games and enhance your user interface with excitement. After reading this short guide, you have sufficient knowledge and skills that can make you able to implement them on your React projects.

## The Usefulness of Adding Fireworks to Your Website
Incorporating firework effects into your website can significantly enhance the user experience by adding a layer of visual excitement and engagement. Fireworks are often associated with celebration and joy, making them an excellent tool for marking special occasions, achievements, or milestones within your application. This can create a memorable experience for your users, making your site stand out.

It is equally possible to improve user interaction and satisfaction by adding fireworks. Firework effects like using buttons or filling out forms could transform an ordinary procedure into an enjoyable one due to its interactivity. It can encourage more usage of your site by luring users to keep coming back thus increasing retention and time spent on your platform.

Also for important events or notifications, fireworks can serve as a powerful visual cue. For example, in a gaming application, you can use fireworks to celebrate a level-up or other big wins which will give instant feedback that feels good to the player. In e-commerce, fireworks can be used to indicate that a person has made a successful purchase or that they have received a special offer thus improving their overall shopping experience.

In addition, the aesthetic appeal of your website can be enhanced through fireworks’ effects. A tastefully arranged fireworks exhibition can add to the theme and branding of your site, thus resulting in a consistent design that is visually appealing. It is a way of improving the general attitude of site visitors towards it therefore making it more refined and a professional appearance.

Above all, incorporating modern technology like firework displays on your website does not entail just an addition of some color or images but enabling its visitors to have an interesting, participatory, and unforgettable encounter such that they will be able to differentiate it from other websites. To come up with a site that has fireworks that are emotionally engaging and visually enticing, an environment that is vibrant and pleasurable to be in is crucial to be developed for clients as well.

## Websites Where You Should Use Firework Effects
If applied, fireworks effects can greatly improve a user’s enjoyment of some websites. Below are some of the appropriate websites where fireworks effects can be used:

Websites that celebrate special events or are used in isolated events such as New Year’s Eve, Independence Day or similar celebrations can easily use fireworks to enhance the celebratory mood. The fireworks visualization increases the celebratory element and makes the event more involving for the visiting audience.

In electronic trading platforms, fireworks can make special offers, flash sales, and show successful operations. One case in point is when a customer completes an order other than during seasonal discounts like black Friday. They attract much fun as well as more involved customers.

 Fireworks in gaming environments can be used for various purposes such as celebrating player achievements, leveling up, or victories. Instantaneous visual feedback creates a gratifying environment thereby improving player satisfaction and retention.

 Fireworks can add excitement and interest to interactive, educational platforms aimed at children, especially when they celebrate milestones or give the right answers. All these can help children learn better and work harder at their tasks.

 Designers, artists, and other creatives sometimes use fireworks to show their work attractively and originally. For example, they can make the fireworks burst out whenever a user hovers over or clicks on a project page to instill a sense of surprise and fun.
 
## Websites Where You Should Not Use Firework Effects
Despite their capacity to hold users’ attention, the fireworks effect may not be appropriate in any kind of website. Below are situations in which one should refrain from doing so:

Websites for professional services businesses, legal firms, and financial institutions must be clean, formal, and focused but the use of fireworks may make users question your seriousness in the company which could look ridiculous.

News websites, academic publications, or websites dedicated to distributing research in general, should focus more on improving readability and accessibility. Users may not concentrate on the content because fireworks force their attention elsewhere.

Healthcare websites, patient services or medical information should have a tranquil and calming design.  Fireworks can be thought of as inappropriate or inconsiderate in such cases where individuals require somber data.

Simpler websites are designed with minimalism in mind, focusing on simplicity and a clear message. However, using fireworks on such pages may distract from their initial idea by making them look overloaded and unsystematic.

## Prerequisites
Before you learn to use Firework Effects in a React app, you must understand [React](https://react.dev/) and [JavaScript](https://www.javascript.com/) basics. To go through this lesson about building and customizing components, one should be aware of React components, state management, and props. Moreover, it would be helpful if you knew how to code in new JavaScript standards [(ES6+)](https://dev.to/cliff123tech/javascript-es6-features-13co) so that it would be easy for you to understand examples and changes made throughout the text.

Establishing a React development environment is another essential requirement; it means that [Node.js](https://nodejs.org/en) and [npm](https://www.npmjs.com/)(Node Package Manager) should be in the machine as well. While these are basic tools used to manage dependencies and work with React apps generally, installing Node.js (that also brings npm as a bonus) offered on their website would be necessary if not done already.

After installing Node.js and npm, you will need to configure your React environment by working with `Create React App` for beginning development. Set up a new React project that follows some common structure and lets you build customer modules It simplifies the initial setup process, allowing you to focus on building your application without worrying about configuration details.

Once you have a basic knowledge of React and JavaScript, as well as an appropriate development environment, you will be ready to follow this guide to successfully integrate Firework Effects to React applications.

## Setting Up the React Project
In the section, your reading will guide you through the initial phases of setting up a React project with fireworks that will be eventually integrated. These involve creating a new React application through the `Create React App` method as well as installing packages that are required.

We will begin with `Create React App`, a commonly used tool, that helps to establish new React projects in a standardized manner by providing structure and configuration that are standard, thereby easing setup at the start. Go ahead, and follow these steps.

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
Afterward, to present fireworks effects, we have to put another library. It is easier to use and customize than other libraries that are available but not used in this guide like [fireworks-js](https://fireworks.js.org/) and has most tutorials about it. We chose to use `fireworks-js` library for this tutorial because of its simplicity and flexibility. You have the possibility of making different fireworks effects with parameters that can be changed as you wish with the help of this particular tool.

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
The initial stage is when we must bring the `fireworks-js` library to our React application. When you are planning on using firework effects, like in `App.js` or a new component file, open up the file then write down this import statement at the beginning:

```javascript
import Fireworks from 'fireworks-js';
```
By stating the above, `fireworks-js` is available to be used in your component.

### Creating a Firework Component
After that, we have to create a Firework Component, the main job of which would be to decide on the way fireworks will be displayed. This one should take care of launching and painting the fireworks animation.

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
We use the `useRef` hook in this component to get a reference to the containing `div`, that will be showing the firework effects. When this component is unmounted, the `useEffect` hook is employed to clear out the firework animation upon mounting and dismounting it.

### Adding the Firework Effect Logic Using the Imported Library
Inside the `useEffect` hook, the Fireworks instance is initialized using both the reference to the container and defined options for firework effects. We ensure that an animation demonstrating fireworks will halt if the component gets removed by use of the `useEffect` hook by returning a cleanup function.

### Rendering the Firework Component in the Main Application
To make the fireworks go off, you must include the fireworks component in our primary app. Locate the `App.js` file and import the Firework component as the first thing in it:

```javascript
import Firework from "./Firework";
```
Then add the Firework component to the [JSX](https://legacy.reactjs.org/docs/introducing-jsx.html) that is returned by the `App` component:

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
You can know that the integration was successful by observing that the fireworks effects have been displayed on the screen after you open your browser and reach `http://localhost:3000`. 

Output:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9f81e256cce80aa6ce4c50f6e6a883f8.gif)

With this, we have successfully added the fireworks effect to our React application. 

## Examples of Popular Websites That Utilize Firework Effects
In this section, we will take a look at examples of some popular websites that utilize fireworks effects. 

### Duolingo
[Duolingo](https://www.duolingo.com/), a famous language-studying website, makes use of the fireworks effect when it comes to commemorating important moments and reaching the target. The application usually represents these animations like fireworks when a user finishes a lesson or makes it to a sequence-based milestone motivating such a person to continue learning.

### Canva
During special promotions or events, [Canva](https://www.canva.com/) occasionally applies a firework effect on its graphic design tool online. For example, Canva can opt to use fireworks during design challenges involving users or when it launches new products to spice up the occasion and increase user involvement.

### Shopify
At times during major events, [Shopify](https://www.shopify.com/ng) implements special effects including Black Friday or Cyber Monday sales using pyrotechnics. Occasionally, pyrotechnics can be set off to recognize successful transactions among other limited-time offers as a way of spurring the excitement in buying things on their websites.

### Twitch
[Twitch](https://www.twitch.tv/), a live streaming platform primarily for gamers, has different visual effects it uses including fireworks during live streams and special events. At important milestones such as reaching a certain number of subscribers or receiving donations (for instance), streamers usually opt for firework animations so that their viewers can be more engaged while watching the broadcast videos.

### Google Doodles
Sometimes, Google incorporates the sparkle effect in its Google logo [Doodles](https://doodles.google/) that involve temporary modifications in the logo on Google’s front page to acknowledge festive seasons as well as remarkable days such as the anniversaries of independence or other celebrated days. An example is when it is New Year’s Eve or Independence Day whereby the Google logo is animated with fireworks to reflect the mood for celebrating those days.

### Github
When events such as [Hacktoberfest](https://github.com/topics/hacktoberfest) or major product launches occur, [Github](https://github.com/) often incorporates fireworks into its routine. Fireworks honor coding technicians, pull requests, or any notable performance in the community for coding software.

### LinkedIn
[LinkedIn](https://www.linkedin.com/login) periodically makes use of fireworks-like effects on its notifications in celebrating user milestones like work anniversaries or new job positions, thereby giving professional achievements a celebratory touch which brings improvements to user satisfaction.

### CodePen
[CodePen ](https://codepen.io/)frequently presents Pens that illustrate how animations can be done. It’s a community for trying out drafts that can increase the attractiveness and interactivity of web pages through firework effects done using [CSS](https://en.wikipedia.org/wiki/CSS) and Javascript. Each user is at liberty to create and distribute explosive animations as a fragment of his/her programming task thus displaying individual abilities as well as inventiveness.

## Conclusion
With this short guide, you are capable of developing firework effects on your React applications to form interesting user experiences. Whenever you are commemorating special occasions, incorporating engaging parts, or just increasing the attractiveness of your undertaking for eyes these fireworks make your interface look much better. 

Thank you and happy coding!