---
sidebar_position: 5
---

# Create Admin Credential

We will create Admin Credential so we can Login to the Game Admin Dashboard, we have not setup the Admin Dashboard yet, but we will do it later.

In order to create Admin Credential, there's few way we can do it, but i have create **simple script** to create that email and password and the token role, for the Game Admin Account Easily, that script is in folder **`/Cloud Function`** prepare to open that folder in Your VSCode.

## Step No.1 Get Service Account

In order to run our **simple script** that we use to create Admin Credential, we need to get the Service Account file from Firebase Console.

- Open your [Firebase Console](https://console.firebase.google.com/), choose your project
- Click on the `Project Settings` button

![T](./assets/Screenshot%202025-01-05%20155829.png)

- Click on the `Service Accounts` tab
- Click on the `Generate New Private Key` button
- Click on the `Generate Key` button

![T](./assets/Screenshot%202025-01-05%20155856.png)

- Download the JSON file
- Copy the JSON file and paste it in the `/Cloud Function/functions/` folders
![T](./assets/Screenshot%202025-01-05%20160504.png)

:::info
you can rename the JSON file to `service-account.json`, so it will be easier to identify the file, because we will copy the file name later.
:::

## Step No.2 Run the Script

To create Admin Credential, we need to run the script, make sure you are in the folder `/Cloud Function/functions/` and run the script by using this command

```bash
npm run setup-firebase
```

:::info
Make sure you are in `/Cloud Function/functions/` folder, if not, you can use `cd functions` to change the directory.
:::

![T](./assets/Screenshot%202025-01-05%20161045.png)

- Choose **Y** to setup the Admin Credential
![T](./assets/Screenshot%202025-01-05%20161054.png)

- After that you will get ask for you service account name, copy your service account file name and paste it, make sure your service account are located in `/Cloud Function/functions/` folder

![T](./assets/Screenshot%202025-01-05%20161113.png)

- After that you will get ask for the Admin Email, you can put any email you want, but make sure it's a valid email

![T](./assets/Screenshot%202025-01-05%20161129.png)

- After that you will get ask for the Admin Password, you can put any password you want, but make sure it's a 6 characters or more

if it's success, you can check your Admin Account in Firebase Console, in the `Authentication` tab, you will see the Admin Account there.

After setup the Admin Credential, you can use that credential to login to the Game Admin Dashboard, but we will have to setup the Admin Dashboard, continue to the next step.
