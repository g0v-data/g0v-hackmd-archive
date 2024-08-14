#  How to Integrate reCAPTCHA v2 into your React Login Forms

Securing login forms is a crucial part of web development today when online threats are becoming more advanced. One effective way of making your login forms more secure is by adding Google reCAPTCHA v2. This article will guide you on integrating reCAPTCHA into your React-based login forms, protecting your application from automated attacks while allowing only valid user access.

## Prerequisites
Before plunging into the amalgamation of reCAPTCHA v2 using your React login forms, have some major determinants in mind. First and foremost, you ought to have a fundamental grasp of React including generating components alongside administering state within a React application. Having prior knowledge of submission handling for forms in React will also serve as an added advantage. 

Apart from React knowledge, you have important tools that need installation and configuration. The main one is the react-google-recaptcha package which can be used as a simple means of adding reCAPTCHA for your React components. A Google account is also a must so that you get access to the Console Admin for reCAPTCHA where you can obtain the site key and the secret key necessary for reCAPTCHA integration purposes. With these prerequisites, there will be a seamless and successful integration process when securing login forms on reCAPTCHA v2.

## Setup
Integrating reCAPTCHA v2 into your React registration form will take you to an initial phase where you need to get some key from Google. First, visit the Google reCAPTCHA website, and then go to the Admin Console. If you haven’t signed in yet, sign in with a Google account. Upon arriving at this Admin Console page, registering your site is required. At this point, you must supply a name for the reCAPTCHA instance and select the specific type of reCAPTCHA that you want. For this integration you choose “reCAPTCHA v2” and click on the “I am not a robot” checkbox option. In addition, you need to include domain names where you want to use reCAPTCHA so that keys will only work on those domains.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a3623bf35b01dc1f9a80c02365da0964.jpg)


At last, accept the reCAPTCHA Terms of Service before making an application. Google provides two prominent codes after the completion of the registration process: site and secret key. The React application utilizes a site key for rendering a reCAPTCHA widget while on the server side, it is used to verify reCAPTCHA responses.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0733843eb20ae5b172bd1abbc59565fa.jpg)

Thus, these codes must be stored securely as they are required later during integration. You may now create your login form with reCAPTCHA as an additional security measure using your site and secret keys.

## Creating a login form
In this stage two, you will create a simple login form that will work as a base for integrating reCAPTCHA. Start by making a basic structure for your React project, ensuring there are components for the login form. The form should have important fields like username or email input and password inputs. You will create the form elements in your React component using ordinary HTML input fields. Each input should be controlled by React state enabling proper management of data in forms. For instance, `useState` hooks can help to track the username and password field values separately. Besides that, you also need a `submit` button to handle if the form is submitted properly. Once you structurally re-design this form, there is a need for a basic validation framework to ensure that users are offering up requirements. For instance, making sure that the two fields representing username and password are not left empty during submission phase of filling them out forms. If you include an `onSubmit` event handler to this form element, the processing of information used for completing the whole framework will be done.

### Implementation
A basic login form designed for user name and password is created using this React component:

```javascript
import React, { useState } from "react";

const LoginForm = () => {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = (event) => {
    event.preventDefault();

    // Basic validation
    if (!username || !password) {
      alert("Please enter both username and password.");
      return;
    }

    // Submit form data (You can add your form submission logic here)
    console.log("Username:", username);
    console.log("Password:", password);
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="username">Username or Email:</label>
        <input
          type="text"
          id="username"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
        />
      </div>
      <div>
        <label htmlFor="password">Password:</label>
        <input
          type="password"
          id="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
      </div>
      <div>
        <button type="submit">Login</button>
      </div>
    </form>
  );
};

export default LoginForm;
```
This code snippet showcases a basic React component designed as a login form containing areas for inputting a username and password. The react’s `useState` hook that oversees states in such cases is the one being utilized; enabling it to listen to whatever is typed in. Two `state` variables are defined via `useState` in this component: username and password - which will be able to hold values for these respective fields. The functions for changing them (`setUsername` and `setPassword`) obtain their respective attributes from related text areas located within said input boxes.

The `handleSubmit` function is activated when a user presses the submit key on the form. Initially, it stops other common behaviors of a browsing architecture like refreshment of the current page after submission occurs sometimes automatically as per instruction by the designer through software programming language code segments. Next, simple checks are conducted whether both name and password columns have been filled out accordingly. If either of them is left blank, a notice appears indicating so and stopping any further presentation of this kind. When there is no mistake in filling the form, the function `handleSubmit` then prints out usernames and passwords to computer logs. This is where you would usually place your code for sending either or all data sets through secure network connections over [TCP/IP](https://) networks to some web server that handles user verification requests.

The form has consolidated data, comprised of two input areas, username/email and password sections. Improving accessibility features is achieved through labeling each input element thus enabling screen readers to understand their purposes. Each input has its `value` attribute set to the relevant state `variable` for synchronization purposes concerning the current states of inputs entered. This means that any changes made by users into these fields will be reflected in states assigned to them. To allow submission, there are `submit` buttons included at last within our form. A click on the submit button initializes `onSubmit` operation on our form leading to the invocation handleSubmit procedure.

Output:

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_8b6facf8ea3ca06dcf8fe8a8861a1f5e.jpg)

Now a basic login form built with React is available which can be improved By Adding reCAPTCHA. The Next steps will require you To add reCAPTCHA in this form so that it distinguishes Humans from Bots successfully.

### The `react-google-recaptcha` package
In the third step, the react-google-recaptcha package will be installed and imported into your React project to include reCAPTCHA on your login interface. In the beginning, you should start by installing the react-google-recaptcha package. To do this, open up your terminal and head to your project’s main folder. Type in one of these commands based on what package manager you’re using:

Using npm:

```bash
npm install react-google-recaptcha
```

or

Using yarn:

```bash
yarn add react-google-recaptcha
```

Thus, the command will make it available for use in your React components after downloading and installing the react-google-recaptcha package to your project.

When you install the package, include the ReCAPTCHA component in your React component file in the login form file. Start with this import statement at the beginning of your file:

```javascript
import ReCAPTCHA from "react-google-recaptcha";
```
This import allows you to utilize the `ReCAPTCHA` component within your login form to embed the reCAPTCHA widget onto your form and execute all necessary verifications. Now that you have installed the package and imported the `ReCAPTCHA` component, it is time to include the reCAPTCHA widget in your login form. Doing so will help keep out automated submissions, only allowing them to be submitted by human beings who are eligible for submission.

## Integrating the reCAPTCHA widget into your login form 
Next, you will integrate a login form with the reCAPTCHA widget and handle its responses when the form is submitted. This step is important for adding an extra layer of security to your form so that only real users can submit it. First off, after importing ReCAPTCHA in your React file, you can use it to add the reCAPTCHA widget by embedding it inside of your [JSX](https://legacy.reactjs.org/docs/introducing-jsx.html) for the login form. In this instance, `sitekey` prop is a site key you obtained from Google during the setup process. Here's how to do that:

```javascript
import ReCAPTCHA from "react-google-recaptcha";

// Inside your component's return statement
<ReCAPTCHA sitekey="YOUR_SITE_KEY" onChange={handleRecaptchaChange} />;
```
The actual site key given by Google should be used in place of "YOUR_SITE_KEY". The `onChange` prop is a function that gets activated once the reCAPTCHA challenge is completed by the user. You will use the function for this to process the response token from the reCAPTCHA.

Subsequently, you should return a response from reCAPTCHA when someone submits their form. The `onChange` method represented would collect the response token as produced by corresponding reCAPTCHA widget upon completion of which its form data are then incorporated within it before being sent into the server.

Here is an example of altering your component that handles retrieving forms:

```javascript
import React, { useState } from "react";
import ReCAPTCHA from "react-google-recaptcha";

const LoginForm = () => {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");
  const [recaptchaToken, setRecaptchaToken] = useState(null);

  const handleRecaptchaChange = (token) => {
    setRecaptchaToken(token);
  };

  const handleSubmit = (event) => {
    event.preventDefault();

    // Basic validation
    if (!username || !password || !recaptchaToken) {
      alert("Please fill out all fields and complete the reCAPTCHA.");
      return;
    }

    // Submit form data, including the reCAPTCHA token
    console.log("Username:", username);
    console.log("Password:", password);
    console.log("reCAPTCHA Token:", recaptchaToken);

    // You would typically send this data to your server here
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label htmlFor="username">Username or Email:</label>
        <input
          type="text"
          id="username"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
        />
      </div>
      <div>
        <label htmlFor="password">Password:</label>
        <input
          type="password"
          id="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
      </div>
      <div>
        <ReCAPTCHA sitekey="YOUR_SITE_KEY" onChange={handleRecaptchaChange} />
      </div>
      <div>
        <button type="submit">Login</button>
      </div>
    </form>
  );
};

export default LoginForm;
```
The instructed script consists of a React component that sets up a login form featuring Google’s reCAPTCHA v2. Its purpose is to ask the user for their login credentials while helping to avoid spam from bots during data compilation. At the start of this script, the `useState` hook is used to keep track of three different states namely: `username`, `password`, and `recaptchaToken`. Each one represents its input field taking as value what has been put through by users and in addition on successful verification via reCAPTCHA an associated token will be generated hence held here.

When a user succeeds in solving the reCAPTCHA challenge, the `handleRecaptchaChange` method gets triggered. It accepts the token as input and with the help of `setRecaptchaToken`, the token is saved in the `recaptchaToken` state variable. Later this token will be sent to the server during form submission to validate whether it was made by a human or not. When once again the user hits the submit button, the `handleSubmit` function is executed. Initially, `event.preventDefault()` is utilized to avoid the normal form submission procedure but afterward, it validates whether username, password, and reCAPTCHA tokens have been filled out or not. In case any of these items are missing an alert comes up and therefore there will be no form submission.

If the form is validated, the `handleSubmit` function will log the username, password, and reCAPTCHA token to the console. In real-world applications, this is where usually you would send the form data including your reCAPTCHA token for further processing and validation on your server. In the `JSX` of the form, there are controlled inputs for both username and password. That is to say that these inputs’ values are tied to the component’s state and any changes made to them are reflected through the onChange event handler. The ReCAPTCHA component gets integrated into the form by setting up `sitekey` prop replaced by the actual site key gotten from Google; and when a user has completed a challenge on there, then the `onChange` prop is assigned `handleRecaptchaChange` function which guarantees that the reCAPTCHA token changes every single time.

Output:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c9294810dcd3b838abc25444bbdd172d.gif)

From the GIF above, our reCAPTCHA widjet have been successfully added to the login form.


## Server-side Verification
In the fifth stage of the procedure, your most important task will be to carry out a server-side validation of the reCAPTCHA token, which enables you to ascertain if the individual who filled out the form went through the reCAPTCHA difficulty. For this purpose, it is wise to do this so that your login system does not fall victim of bots. When a user submits a form, your server gets back both client-side generated reCAPTCHA as well as other form details sent along with it by Google’s recaptcha API enabling them check out whether such tokens belong to humans or bots. The following describes how server-side verification is carried out:

### Send the Token to Your Server
To your server POST request with username, password, and reCAPTCHA token will come from the client when you submit the form. Such requests can be handled by frameworks like [Express.js](https://expressjs.com/) in Node. The following is an illustrative example of how the client transmits data:

```javascript
fetch("/api/login", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    username: username,
    password: password,
    recaptchaToken: recaptchaToken,
  }),
}).then((response) => {
  // Handle the response from the server
});
```
The code above indicates a JavaScript `fetch` request for sending data from clients (mostly web browsers) to servers. During the login process, it is among the requests whereby the server checks on the user’s credentials and reCAPTCHA token. The `fetch` function is a modern way to perform HTTP requests on the client side. Here, it sends out a `POST` request to `/api/login` endpoint. Generally, the `POST` method is used for sending the information to the server and subsequently processed. It also includes header objects indicating what type of content will accompany it. In this case, `Content-Type` has been changed into `application/json` which means that information within a request body is in JSON format.

To transmit this information to our server add it to the property body meant for it. This data will be coming from `JSON.stringify` thus transforming the JavaScript object containing `username`, `password` and `recaptchaToken` into a string in a JSON format used while communicating with the server that expects all data in JSON format meaning that formatting it correctly as `JSON.stringify` is essential. After sending out a request via .then, the server’s response is handled within the function given to .then. Such things may include checking if the login was successful or handling errors returned by the server. It is important to handle responses because they provide feedback to users or allow them to take other actions based on verification results from server-side systems for authentication purposes.

### Verify the Token on the Server
To examine the token, on the server, you must use the reCAPTCHA secret key acquired during the initial setup. A request will be sent to Google’s reCAPTCHA verification API will have the token and your secret key as parameters. Here is an illustrative example of server-side verification using Node.js and Express:

```javascript
const express = require("express");
const fetch = require("node-fetch");
const app = express();

app.use(express.json());

app.post("/api/login", async (req, res) => {
  const { username, password, recaptchaToken } = req.body;

  // Verify the reCAPTCHA token
  const secretKey = "YOUR_SECRET_KEY";
  const verificationUrl = `https://www.google.com/recaptcha/api/siteverify?secret=${secretKey}&response=${recaptchaToken}`;

  const response = await fetch(verificationUrl, { method: "POST" });
  const data = await response.json();

  if (data.success) {
    // reCAPTCHA was successful, proceed with login logic
    res.json({ success: true, message: "Login successful" });
  } else {
    // reCAPTCHA failed, reject the login attempt
    res
      .status(400)
      .json({ success: false, message: "reCAPTCHA verification failed" });
  }
});

app.listen(3000, () => console.log("Server running on port 3000"));
```
The stated code snippet exhibits a simple server built using node.js that utilizes an Express framework to cater for a Post request associated with login operation having reCAPTCHA verification. Thereafter, the required modules including express (for developing servers) and node-fetch (for making HTTP requests) were imported. In this case, Google’s Recaptcha Verification API. An Express application is created using `express()` and assigned to the variable app. Through this middleware, all communications are in JSON format so that our server can handle upcoming JSON data.

The login endpoint is expressed in a POST method at `/api/login` by the server. Thus, when a request is sent to this endpoint, it expects a JSON object containing the `username`, `password`, and `recaptchaToken`. Destructuring extracts these values from the request body. The next code verifies the reCAPTCHA token. The server constructs the verification URL by adding a secret key that you obtained from Google when setting up reCAPTCHA and recaptchaToken received from the client. This URL is used for sending POST request to Google’s reCAPTCHA verification API.

To send this POST request to the Google API, the fetch function is used. Since this is an asynchronous operation, the await keyword is employed to suspend execution until a response has been obtained. Then, the response from Google is transformed into a JSON object via await `response.json()`. The server afterward checks if true or false `data.success` property from the response received from Google is true or false. If true, it means that reCAPTCHA verification was successful and hence indicated that it is human being who submitted forms. Following up could be additional logins logic like comparing username and password with those stored in a database, thereafter sending out JSON object with indication of success.

Should the condition `data.success` be set to false, this implies that reCAPTCHA verification has failed and hence the server rejects the login attempt. It sends a [400 status code](https://umbraco.com/knowledge-base/http-status-codes/#:~:text=) (which refers to a bad request) along with a JSON object which notifies the client that reCAPTCHA verification has been unsuccessful. The last line `app.listen(3000`, `() => console.log('Server running on port 3000'))` starts the server on port 3000 where it listens to incoming requests for the same. When the server runs, it logs a message informing that it’s ready and available to accept requests.

### Handle the Verification Response
If the token is valid, the verification API response will have a success field. If the success response confirms then the user‟s credentials can be authenticated by checking it against your database for example username and password as these are always common. However, if the verification fails then you must reject the login attempt and let them know that reCAPTCHA verification did not succeed.

Output:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_db777c8dadd8918845237eb01feaf6e1.gif)

In brief, this server-side verification process is essential for ensuring that a reCAPTCHA token is real and that the form submission came from a human. It is possible to minimize the risk of attacks by bots using Google’s API because you will be validating the token securely thus adding another level of security in your login form.


## Conclusion
To sum up, it is very secure to have Google ReCAPTCHA v2 on your React login forms to block automated bots and malicious attacks. Here we have looked at how logging in can help you gain the reCAPTCHA keys you need, build a simple login page, add and configure the reCAPTCHA component in the app as well and handle verification of the reCAPTCHA token on the server side.