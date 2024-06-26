# ReachInBox Assignment

## Project Overview

The ReachInBox Assignment is a server-side application built using Node.js and Express.js. Its primary goal is to facilitate email parsing and management for Google and Outlook accounts. The application leverages advanced AI functionalities from OpenAI, integrates with Google APIs for Gmail services, and utilizes Microsoft Graph API for Outlook integration. Task scheduling is handled efficiently using BullMQ.

![image](https://github.com/Pranshu820/ReachInbox.ai-Email-Tool/assets/75555961/435302e3-77ba-4269-bb90-9338ba672c50)


## Deployment Links

- **Frontend:** [ReachInBox Assignment Frontend](https://reach-inbox-assignment.vercel.app/)
- **Backend:** [ReachInBox Assignment Backend](https://reachinbox-assignment-4rf9.onrender.com)
- **API Documentation (Postman):** [API Documentation](https://documenter.getpostman.com/view/31971527/2sA35D43FE)

## Technologies Used

- Node.js
- Express.js
- OpenAI
- Google APIs
- Microsoft Graph API

## npm Packages Used

- dotenv
- Axios
- bullMQ
- google-auth-library
- ioredis
- @microsoft/microsoft-graph-client
- @azure/msal-node

<br>

## Installation setup

1. Clone the repository to your local machine

```bash
git clone https://github.com/Pranshu820/ReachInbox.ai-Email-Tool
```

2. Navigate to the root directory of the project directory :

```bash
cd backend
```

3. Run `npm install` to install all the dependencies
4. Create a `.env` file in the root directory with the same IDs as specified in the documentation.

## Running the server

1. To start the server, run the following command in your terminal

```bash
npm start
```

_This will start the server at localhost:5000 (or whatever port you have specified)._
or we can use backend deployed link also.

2. To start the worker.js file, run the following command in your terminal

```bash
npm run server
```

## API Endpoints

### For Google's OAuth2.0:

- `https://reachinbox-assignment-4rf9.onrender.com/auth/google` - GET for google authentication
- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/userInfo/:email` - GET request to view user profile
- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/allDrafts/:email` - GET request to view all drafts mail.
- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/read/:email/message/:message` - GET request to read a specific email(using id).
- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/list/:email` - GET request to get a list of mails.
- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/sendMail` - POST request send mail with label.

```
{
    "from":"sendersmail@gmail.com",
    "to":"recieversmail@gmail.com",
    "label":"interested/not-interested/more-information"
}
```

- `https://reachinbox-assignment-4rf9.onrender.com/api/mail/sendone/:id` - POST request to send a single mail for particular ID.

```
{
    "from":"sendersmail@gmail.com",
    "to":"recieversmail@gmail.com"
}
```

- - `https://reachinbox-assignment-4rf9.onrender.com/api/mail/sendMultiple/:id` - POST request to send a single mail for particular ID.

```
{
   "from":"sendersmail@gmail.com",
   "to":["demo@gmail.com","demo@gmail.com", "demo@gmail.com"]
}
```

### For microsoft azur's OAuth2.0:

- `https://reachinbox-assignment-4rf9.onrender.com/outlook/signin` - GET for micosoft azur authentication for outlook
- `https://reachinbox-assignment-4rf9.onrender.com/outlook/callbak` - GET for micosoft azur getting access token
- `https://reachinbox-assignment-4rf9.onrender.com/outlook/profile` - GET request to get profile data for particular user
- `https://reachinbox-assignment-4rf9.onrender.com/outlook/all-Mails/{email}` - GET request for get ist of all mails of outllok user
- `https://reachinbox-assignment-4rf9.onrender.com/outlook/{email}/read-Msg/{:message}` = GET request to read partivcular mail using messange id
- `https://reachinbox-assignment-4rf9.onrender.com/outlook/{email}/send-Mail` - post request for sending mail to another user using outlook

```
{
    "from":"sendersmail@gmail.com",
    "to":"recieversmail@gmail.com"
     "label":"interested/not-interested/more-information"
}
```

- `https://reachinbox-assignment-4rf9.onrender.com/outlook/sendone/:email/:id` - post request for sending mail to another user using outlook using `bullmq`

```
{
    "from":"sendersmail@gmail.com",
    "to":"recieversmail@gmail.com"
}
```

## Sample .env sample:

```
PORT = ***
GOOGLE_CLIENT_ID = ***
GOOGLE_CLIENT_SECRET = ***
GOOGLE_REDIRECT_URI = ***
GOOGLE_REFRESH_TOKEN = ***
OPENAI_SECRECT_KEY = ***
redis_port = ***
redis_host = ***
redis_pass = ***
AZURE_CLIENT_ID = ***
AZURE_CLIENT_SECRET = ***
AZURE_TENANT_ID = ***
```
