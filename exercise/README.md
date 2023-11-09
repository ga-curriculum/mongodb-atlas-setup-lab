# ![[MongoDB Atlas Setup Lab] - Exercise](./assets/hero.png)

tktk The purpose of this lab is to register for a MongoDb Atlas account to utilize for creating non-relational databases.

## Create an Atlas Account

The most popular service for hosting MongoDB databases, not surprisingly, is MongoDB's own [Atlas](https://www.mongodb.com/atlas/database). We'll use it to host all of our MongoDB databases in class.

First, you will need to sign up for a free account [here](https://www.mongodb.com/cloud/atlas/register).

![Atlas Sign Up](./assets/atlas-sign-up.png)

As seen in the image above, you will have **two different options** to sign up:

1. Click Sign up with Google (***blue highlighted button***)
2. Enter the required information, agree to the Terms of Service, and click Create your Atlas account. (***red highlighted inputs and button***)

Choose **one** of the following **two (2) options** to proceed:

### Option 1: Sign up ***WITH*** Google
<details>

<summary>
    Click here
</summary>

### Signing up ***WITH*** Google

Click the **Sign up with Google** button.

Read the Terms of Service and Privacy Policy, then agree to them.

Select the **Submit** button.

![Atlas Google Terms of Service](./assets/google-tos.png)

Proceed to the **'Welcome to Atlas'** section below.

</details>

### Option 2: Sign up ***WITHOUT*** Google

<details>
<summary>
    Click here
</summary>

### Signing up ***WITHOUT*** Google

1. Provide the **required information**. You should store this username and password somewhere easily accessible and secure (like a password manager).
2. Read the **Terms of Service** and **Privacy Policy**, then agree to them.
3. Finally select the **Create your Atlas acount** option.

If you created an account without using Sign up with Google, you'll be taken to a page asking you to verify your email, as shown below.

![Atlas Email Verification](./assets/email-verification.png)

Find the email from MongoDB in your inbox and verify your email.

After you've verified your email, you'll be taken to a page informing you that you've successfully verified your email and a **Continue** button.

Click the **Continue** button.

Proceed to the **'Welcome to Atlas'** section below.

</details>

## Welcome to Atlas

Answer the marketing questions however you'd like. Some suggestions are shown below, but your selections do not impact your experience.

Select the **Finish** button when you're done.

![Atlas Marketing](./assets/marketing.png)

## Deploy Your Database

It's time to set up the cluster!

Clusters are MongoDB's way of collecting your databases all in one place.

Select the **M0** option, which is ***FREE***.

Select **AWS as the Provider**, and select the **Region** closest to your job market.

Name your cluster whatever you want, but know that this name cannot be changed later. Ensure that the text directly above the **Create** button says **FREE**.

***Do not select the*** **Create** ***button unless this text says*** **FREE.** If it has a dollar amount, review your selections and ensure you have correctly configured the service from this page.

Finally, select the **Create** button.

![Atlas AWS](./assets/aws.png)

## Security Quickstart

You will be taken to a ***Security Quickstart*** page. There will be a message at the bottom left stating that the database cluster is being provisioned, along with the approximate amount of time it will take to complete.

While the cluster is provisioned, create a **database user** (*different from your account user*) by following the steps in the **'How would you like to authenticate your connection?'** section.

The database user's credentials you create now must be **embedded** in the **connection string** used to connect to the database, which you will retrieve soon.

Select a **username** and **password**. The username and password must be **alphanumeric**. They **cannot** contain any characters that are not English letters or numbers. **Do not** use special characters of any kind, including spaces.

Feel free to use the **Autogenerate Secure Password** option if you would like or use the default selections; it will only build passwords that meet this constraint.

It is vital that you store this username and password somewhere easily accessible and secure (like a password manager). Use the provided **Copy** button to ensure you have an exact copy of your chosen password. **You are going to need access to this information soon.**

After you have selected a username and password, select **Create User**.

![Atlas Security Quickstart 1](./assets/security-quickstart-1.png)

The page should look like this after the above step:

![Atlas Security Quickstart 1 Complete](./assets/security-quickstart-1-complete.png)

Scroll down to the second step: **Where would you like to connect from?**

In the IP Address field, enter the text **0.0.0.0/0** exactly as shown here.

In the description, write **Anywhere**.

Then click the **Add Entry** button.

> ❗️ IMPORTANT: This is ***NOT*** a suitable setting in a production environment and means that your database can be accessed from any device that has the correct username and password combination. We are using this setting to ensure you can easily develop and deploy to aid your educational experience. For this reason (among others), it is imperative that you not store personally identifying information (phone numbers, addresses, credit card numbers or details, insurance identification, your lucky numbers, etc. in your database.)

![Atlas Security Quickstart 2](./assets/security-quickstart-2.png)

The page should look like this after the above step.

Select the **Finish and Close** button and then the **Go to Overview** button in the pop-up.

![Atlas Security Quickstart 2 Complete](./assets/security-quickstart-2-complete.png)

## Obtain the Connection String

**IMPORTANT:** Database connection strings ***contain*** the **username** and **password** for connecting to the database. **NEVER** include the connection string in the project's source code - use a `.env` file instead.

You will arrive on the **Overview** page. To obtain the connection string that will be added to a project's `.env` file, click the **Connect** button as shown below:

![Atlas Overview](./assets/atlas-overview.png)

Select the only option under the **Connect to your application** header, **Drivers**:

![Atlas Connection Methos](./assets/connection-method.png)

Click the **'copy'** button to add the connection string to your clipboard. You do not need to do anything else on this page.

![Atlas Connection String](./assets/connection-string.png)

## Use the Connection String in Your App

> ❗️ Please do not attempt to use any of the connection strings below; they will not function in your applications.

You're almost done, but you ***MUST*** update the connection string with a few changes:

1. Replace `<password>` (including the `<` and the `>`) with the **password** of the database user you created earlier.

    For example, using the password `my2Tacos` along with the connection string above as an example, the connection string would look like this after making this change:

    ```bash
    mongodb+srv://student:my2Tacos@student-cluster.uwdsn12.mongodb.net/?retryWrites=true&w=majority
    ```

2. **IMPORTANT:** The connection string does not include a database name by default. You'll add an appropriate database name between the `/?` part of the connection string for each project. For example, if you have a project named `my-project`, you could give the database the same name:

    ```bash
    mongodb+srv://student:my2Tacos@student-cluster.uwdsn12.mongodb.net/my-project?retryWrites=true&w=majority
    ```
You're good to go!

You can now paste the connection string in an application's `.env` file, assigning it to a **DATABASE_URL** environment variable. As an example:

```bash
DATABASE_URL=mongodb+srv://student:my2Tacos@student-cluster.uwdsn12.mongodb.net/my-project?retryWrites=true&w=majority
```

You can use this database connection string for multiple projects. If you plan to do so, save the copied database connection string in a safe place for future reference! 

For future projects, if you do use the same connection string, just be sure to change the ***database name*** part of the connection string, as mentioned above. For example, if you were to build a **flights** app, you might have a connection string that looks like this:

```bash
mongodb+srv://student:my2Tacos@student-cluster.uwdsn12.mongodb.net/flights?retryWrites=true&w=majority
```

And if you were to build a **tacos** app, you might have a connection string that looks like:

```bash
mongodb+srv://student:my2Tacos@student-cluster.uwdsn12.mongodb.net/tacos?retryWrites=true&w=majority
```

**All that changes is the text between the `/` and the `?` towards the end of the connection string!**

## Viewing & Editing Data

You can use Atlas to view and edit data by clicking on the **Browse Collections** button on the **Database Deployments** page, as shown below.

MongoDB also maintains an application called Compass that lets you browse your data on Atlas with just your connection string. You can download Compass [here](https://www.mongodb.com/try/download/compass).

![Atlas Browse Collections](./assets/browse-collections.png)

Congrats, you are now ready to create databases in MongoDB Atlas! 🎉
