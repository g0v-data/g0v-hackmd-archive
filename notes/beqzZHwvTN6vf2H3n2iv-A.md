# How to Integrate Google Speech-to-Text API into Your Application- DevrelSquad

`banner img here`

## Overview 
Google Cloud Platform is one of the famous cloud service providers in the market. With cloud features focusing on deployment and storage, GCP also provides features like speech recognition.Integrating the google cloud speech to text API in your application will enchance your app user expereince.This robust API allows developers to integrate accurate and real-time speech recognition capabilities into their applications.Google Speech-to-Text API provides a reliable solution, whether it’s for transcription services, voice-controlled applications, or language processing tasks. 

### Getting Started 
To integrate Google Speech-to-Text API into a web application using JavaScript, you need to follow these steps: 

#### Step 1: Set Up Google Cloud Platform
To setup the speech to text we need to get google API key first, for that we've to go <a href="https://console.cloud.google.com/">Google Cloud Console.</a>

![image](https://hackmd.io/_uploads/ry7ZDwJrA.png)

- Click on the project drop-down and select "New Project".
- Enter a name for your project and click "Create".

![image](https://hackmd.io/_uploads/S1_zqvySA.png)


- Go to the Cloud <a href="https://console.cloud.google.com/marketplace/product/google/speech.googleapis.com">Speech-to-Text API</a> service page.
- In the Cloud Console, navigate to APIs & Services > Library.
- Search for "Speech-to-Text API" and click on it.
- Click "Enable".

![image](https://hackmd.io/_uploads/Bk1KjvJSR.png)

- Go to APIs & Services > Credentials.
- Click on "Create Credentials" and select "Service Account".
- Fill in the required details and click "Create".
- On the next page, assign the "Project > Editor" role and click "Continue".
- Click "Done".
- Click on the created service account and then "Add Key".
- Select "JSON" and click "Create". A JSON file will be downloaded.

![image](https://hackmd.io/_uploads/SJ8FRPJr0.png)

### Step 2: Create a Backend Server 
##### Using Node.js and Express

1. Intialize a node js project 

![nodejs project cmd (2)](https://hackmd.io/_uploads/S192-OyHR.png)

2. Create the server script 
3. Save the service account JSON file to your project directory, e.g., service-account-file.json.

![server script](https://hackmd.io/_uploads/ryWzGdJr0.png)

3. Run the server 

`node server.js` 

### Step 3: Create the Front-End

1. Create an HTML file

![htmlcodes](https://hackmd.io/_uploads/rkz0QO1rC.png)

You can use a simple server like http-server to serve the HTML file, or integrate it into your existing server setup.

**Run the server to check**, Open your browser and navigate to your front-end HTML file (you might need a local server to serve your HTML file, such as using http-server).


### Step 4: Testing

-    Open your browser and navigate to http://localhost:3000.
 -   Click "Start Recording" and speak into your microphone.
  -  Click "Stop Recording" and wait for the transcription to appear.

#### Important Notes

- Service Account Key: The keyFilename in the SpeechClient configuration should point to the service account JSON file. This is where your credentials are stored.

- Secure Your Backend: Ensure your backend is secure and only accessible to authorized clients to prevent misuse.
- Ensure CORS is properly configured if you're making cross-origin requests.
- This example uses recorder.js for capturing audio. You can use other libraries if needed.
- Make sure to secure your backend API to prevent unauthorized access.
