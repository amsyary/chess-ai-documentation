---
sidebar_position: 1
sidebar_label: Setup Web Admin Dashboard
---

# Setup Web Admin Dashboard

Admin Dashboard is a web-based control panel designed to manage and monitor your livestreaming app, that contains features like user management, streaming control, settings & configuration, and more.

Our Admin Dashboard is build on React JS with Typescript, and Shadcn UI for the UI components.

## Prerequisites

Before starting, you need to have the following installed:

- Node.js

## Step 1: Install dependencies

1. Open a terminal and navigate to your `/MegooLiveAdmin` directory, and install all the dependency :

```
npm install
```

## Step 2. Create .env file

1. Create a new file named `.env` in the root of your project `/MegooLiveAdmin` directory.

2. Copy the content of `.env.example` file and paste it in the `.env` file.

![Copy .env.example file](./assets/Screenshot%202025-01-06%20103708.png)

we need to fill all the variables in the `.env` file, we canget that from our Firebase Project

3. Open your [Firebase Console](https://console.firebase.google.com/) and go to the `Project Settings` tab.

4. From Firebase Console Dashboard, click Plus Button to create a new App

![Create new App](./assets/Screenshot%202025-01-06%20105238.png)

5. Choose Web as the platform and click Next

![Choose Web](./assets/Screenshot%202025-01-06%20105302.png)

6. Fill the App Name and click Next

![Fill App information](./assets/Screenshot%202025-01-06%20105333.png)

7. After that you will get the Firebase Config, copy each of the variable according to the `.env` file.

![Firebase Config](./assets/Screenshot%202025-01-06%20105608.png)

for example:

```
VITE_FIREBASE_API_KEY=AszdfaSyAaa62jdwfafga33dfsasfrer4dasdf
```

## Step 3. Run the Admin Dashboard

After setting up the `.env` correctly, now you can run the Admin Dashboard locally using the following command:

```
npm run dev
```

![Run Admin Dashboard](./assets/Screenshot%202025-01-06%20110646.png)
it should look like this

you can now open the URL that you get from the terminal, and log in using your email and password that you previously set up in the [Create Admin Credentials](../setup-firebase/create_admin_credential) tab.

![Admin Dashboard](./assets/Screenshot%202025-01-06%20110723.png)

:::info
If it's just blank, it means that the `.env` file is not set up correctly, check the console to see the error.
:::

Now you use the Admin Dashboard to manage your livestreaming app.

![Admin Dashboard](./assets/Screenshot%202025-01-06%20110739.png)

:::info
To help you develop and maintain the admin dashboard more efficiently, we've set up Plop.js as a code generator. You can use the `npm run plop` command to automatically generate various components and features:

1. To generate a new page:
   - Run `npm run plop`
   - Select "page" from the menu
   - Enter the page name
   - This will create a new page with proper routing and basic structure

2. To generate Redux state management:
   - Run `npm run plop`
   - Select "redux" from the menu
   - Enter the feature name
   - This will create actions, reducers, and selectors with proper TypeScript types

3. To generate a new component:
   - Run `npm run plop`
   - Select "component" from the menu
   - Enter the component name
   - This will scaffold a new React component with proper styling

![Plop](./assets/Screenshot%202025-01-06%20113421.png)

The generated code follows best practices and maintains consistency across the codebase. This saves development time and reduces boilerplate code.
:::

- After you can run the Admin Dashboard locally, in the next Step, we will Deploy that Admin Dashboard to Firebase Hosting.
